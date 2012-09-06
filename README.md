Copy errol.jar into the "libs" folder in your Android project in Eclipse. If you're using an older version of Android build, you may need to add the jar file to your build path (http://stackoverflow.com/questions/3280353/how-to-import-a-jar-in-eclipse).

In the onCreate of your main activity you need to call:
EventLog.initialize(this, "YOUR_API_KEY_HERE");
You also need to "import package com.sonalight.analytics.api;" at the top

Every time you want to track something, call EventLog.logEvent("EVENT_IDENTIFIER_HERE");
You also need to "import package com.sonalight.analytics.api;" at the top of every file you call this in.

Event upload happens every 10 events and every 10 seconds. After putting in the code and running it, you should see stuff pop up on the site right away.

You also want to call EventLog.uploadEvents() whenever the entire app may get killed by the system (eg in the onDestroy of every activity where there are no background services.)

Finally, in order to track sessions, include EventLog.startSession() in every onResume() in every activity and EventLog.endSession() in every onPause() in every activity in your app.