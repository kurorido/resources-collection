# Reference

* ResultReceiver
  * https://github.com/googlesamples/android-play-location/blob/master/LocationAddress/app/src/main/java/com/google/android/gms/location/sample/locationaddress/FetchAddressIntentService.java
* LocalBroadcastReceivers

# Steps use ResultReceiver

* Add ResultReceiver members
```
protected ResultReceiver mReceiver;
```

* Get Receiver from intent in onHandleIntent()
```
mReceiver = intent.getParcelableExtra(Constants.RECEIVER);
```

* Deliver Result
```
deliverResultToReceiver(Constants.SUCCESS_RESULT,
                    TextUtils.join(System.getProperty("line.separator"), addressFragments));
                  
private void deliverResultToReceiver(int resultCode, String message) {
    Bundle bundle = new Bundle();
    bundle.putString(Constants.RESULT_DATA_KEY, message);
    mReceiver.send(resultCode, bundle);
}
```
