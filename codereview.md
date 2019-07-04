##Code review Rules

# declare a variable and method with final if you think this method or varibale will not change for further.  
       public final void invokeJobExecutor(final String jobName) {
    LOGGER.info("invoking the scheduleJob : {}", jobName);
    final Instant startedAt = Instant.now();
    final Optional<ScheduleGenerationJobDetail>  scheduleJob = waveParameterRepositoryService
        .findJobDetailsByJobName(jobName);
        }
  
  # Meaningful Names . 
            ex:   int d; // elapsed time in days
                     
                     or 
                  int elapsedTimeInDays;
  
  
     public List<int[]> getThem() {
     List<int[]> list1 = new ArrayList<int[]>();
     for (int[] x : theList)
       if (x[0] == 8)
         list1.add(x);
     return list1;
   }
   
   above code problem is
   1) What kind of things are in theList?
   2) what is significance of the zeroth subscript of an item in theList?
   3) What is the significance of the value 8?
   4) How would i use the list begin returned?
   
   Soln: 
   public List<int[]> getFlaggedCells() {
       List<int[]> falggedCells=new ArrayList<int[]>();
       for(int[] cell : gameboard)
       if(cell[STATUS_VALUE]==FAGGED)
              flaggedCells.add(cell);
              return falggedCells;
                 
   }
   
  
