# CleanCode

Use Predicate for validations
  
  Ex:   Need to validate isNotNull or Size is greater than zero.  
  Predicate<TripEvents> istripeventsexists = ev -> ( ev != null && ev.getTripEvents().size() > 0) ;  
  
  Ex: Predicate<Event> isEventPublished = ev -> (eventPublisher(ev) == HttpStatus.ACCEPTED) ;
  
Use Functional Programming 
 Function<TripEvents, TripEvents> eventStreamPublisher = te -> {
      te.getTripEvents().removeIf(isEventPublished) ;
//    
//    te.getTripEvents().forEach(ev -> {
//       if( eventPublisher(ev != HttpStatus.ACCEPTED)){
//          
//       }
//    });
      return te ;
   } ;


How to use above two features in method  
 private void publishEventToTracking(Event event){
      TripEvents pendingTripEvents = getPendingEventsNotSentToTAPI(getEventDocID(event));
      if(isEventPublished.test(event) ){
         if(istripeventsexists.test(pendingTripEvents)){
            pendingTripEvents = eventStreamPublisher.apply(pendingTripEvents);
            if (!arePendingEventsPresent.test(pendingTripEvents)) {
               logger.info("Deleting the pending Trip Events Document: "+getEventDocID(event)) ;
               deleteDocumentFromCouchbase(getEventDocID(event));
               return;
            }
         }
      } 
      return;
   }
