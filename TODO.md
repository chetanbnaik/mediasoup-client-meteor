# TODO

* I don't like that sender.id matches any track.id since it may be replaced later, etc.

* DLS role stuff.



## Join flow

* App creates a `Room` via `room = new Room()`.

* App calls `room.join()`.
  * App generates its local RTP capabilities and local DTLS params for sending and receiving (local parameters).
  * `room` emits "sendcommand" (command "join" with local parameters) and app sends it to mediasoup.
  * mediasoup replies with its RTP capabilities, remote DTLS params for receiving and sending, and remote ICE params (remote parameters).
  * App and reduces its local RTP capabilities with the remote ones.
  * `join()` resolves.

* Local parameters are as follows:

```js
localParameters :
{
  rtpCapabilities    : {},
  sendDtlsParameters : {},
  recvDtlsParameters : {}
}
```

* Remote parameters are as follows:

```js
remoteParameters :
{
  rtpCapabilities    : {},
  recvDtlsParameters : {},
  sendDtlsParameters : {},
  recvIceParameters  : {},
  sendIceParameters  : {}
}
```