Code review Rules

1) declare a variable and method with final if you think this method or varibale will not change for further.  
       public final void invokeJobExecutor(final String jobName) {
    LOGGER.info("invoking the scheduleJob : {}", jobName);
    final Instant startedAt = Instant.now();
    final Optional<ScheduleGenerationJobDetail>  scheduleJob = waveParameterRepositoryService
        .findJobDetailsByJobName(jobName);
        }
    
