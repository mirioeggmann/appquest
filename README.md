# App Quest

![HSR](http://appquest.hsr.ch/images/fho.png)

## App Quest 2016 - Android

### About
The [App Quest](http://appquest.ch/) is an event of the [HSR](https://www.hsr.ch/Home.home.0.html) where you can learn or practice programming apps for android or ios. In 12 weeks you have to program 5 applications and in the end of the event you can use them to win the Treasure Hunt and earn some cool stuff.

### General

|   |  |
|---|---|
| Team | MeIsTeam |
| Team members | [Mirio Eggmann](https://github.com/mirioeggmann), [Timon Borter](https://github.com/bbortt) |
| Employer | [PostFinance AG](https://www.postfinance.ch/) |
| Coach | [Rafael Krucker](mailto:rkrucker@hsr.ch) |
| Organizer | [Mirko Stocker](https://github.com/misto) |
| Operating System | Android |
| Required Apps | [AppQuest Logbuch](http://appquest.hsr.ch/logbuch.apk), [Barcode Scanner](https://play.google.com/store/apps/details?id=com.google.zxing.client.android)|

### Apps
Apps will be public when the AppQuest 2016 is over.

- [x] 1. App [Metal Detector](https://github.com/mirioeggmann/appquest-metal-detector) (deadline: none)
- [x] 2. App [Memory](https://github.com/mirioeggmann/appquest-memory) (deadline: 8.10.2016)
- [x] 3. App [Treasure Map](https://github.com/mirioeggmann/appquest-treasure-map) (deadline: 29.10.2016)
- [x] 4. App [Pedometer](https://github.com/mirioeggmann/appquest-pedometer) (deadline: 19.11.2016)
- [x] 5. App [Pixel Painter](https://github.com/mirioeggmann/appquest-pixel-painter) (deadline: none)

### Given code snippets

[ZXing Barcode Scanner](https://gist.github.com/misto/3938337#file-gistfile1-java)
```java
private static final int SCAN_QR_CODE_REQUEST_CODE = 0;

@Override
public boolean onCreateOptionsMenu(Menu menu) {
	MenuItem menuItem = menu.add("Log");
	menuItem.setOnMenuItemClickListener(new OnMenuItemClickListener() {

		@Override
		public boolean onMenuItemClick(MenuItem item) {
			Intent intent = new Intent("com.google.zxing.client.android.SCAN");
			intent.putExtra("SCAN_MODE", "QR_CODE_MODE");
			startActivityForResult(intent, SCAN_QR_CODE_REQUEST_CODE);
			return false;
		}
	});

	return super.onCreateOptionsMenu(menu);
}

@Override
public void onActivityResult(int requestCode, int resultCode, Intent intent) {
	if (requestCode == SCAN_QR_CODE_REQUEST_CODE) {
		if (resultCode == RESULT_OK) {
			String logMsg = intent.getStringExtra("SCAN_RESULT");
			// Weiterverarbeitung..
		}
	}
}
```

---

[Logbuch](https://gist.github.com/misto/3938488#file-gistfile1-java)
```java
private void log(String qrCode) {
	Intent intent = new Intent("ch.appquest.intent.LOG");

	if (getPackageManager().queryIntentActivities(intent, PackageManager.MATCH_DEFAULT_ONLY).isEmpty()) {
		Toast.makeText(this, "Logbook App not Installed", Toast.LENGTH_LONG).show();
		return;
	}

	// Achtung, je nach App wird etwas anderes eingetragen
	String logmessage = ...
	intent.putExtra("ch.appquest.logmessage", logmessage);

	startActivity(intent);
}
```

## License
[MIT License](https://github.com/mirioeggmann/appquest/blob/master/LICENSE)
