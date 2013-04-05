# must.js

Pipe community into your browser with the Meetup Streaming API

## Usage

This client provides a interface for both websocket and long-polling
protocols. You supply a callback function to respond to the json,
and any parameters you want to be included. For example, to alert
with the member_id for every RSVP in the event "1234":

### Loading

You will want to make sure the client is loaded, once

You can either load it immediately

     $(window).load(must.Loader.load);

Or defer is loading

     $(window).load(must.Loader.defer(function() {
        // do after deferral
     }));

### Streaming

After loading you can start streaming meetup data

#### RSVPs

      must.Rsvps(function(json) {
          alert(json.member.member_id);
      }, { event_id: 1234 });

#### Comments

     must.Comments(function(json) {
        alert(json.comment);
     });

#### Photos

    must.Photos(function(json){
      alert(json.highres_link);
    });

#### Checkins

    must.Checkins(function(json) {
      alert(json.member.member_name);
    }, {
      event_id: 1234
    });

### Stopping stream

If you ever wish to stop the cycle of callbacks, call `stop()`
on the object returned by a streams creation.

      stream.stop();

To restart the stream, create a new one with the function above.


### Rate limitations

The Meetup stream api allows up to 10 concurrent connections from the same client IP.

This client requires jQuery 1.4 or higher.

Meetup 2013

