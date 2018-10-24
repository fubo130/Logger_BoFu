Tasks to answer in your own README.md that you submit on Canvas:

1.  See logger.log, why is it different from the log to console?
	Ans: In logger.properties we can find that the ConsoleHandler.level for console is "INFO", and in the logger.log file the FileHandler.level is "ALL" and that cause we don't have the ExecutionCondition in our console but has that in the logger.log file. If we change the level in console to "ALL", the console will print the same thing with logger.log file.
1.  Where does this line come from? FINER org.junit.jupiter.engine.execution.ConditionEvaluator logResult Evaluation of condition [org.junit.jupiter.engine.extension.DisabledCondition] resulted in: ConditionEvaluationResult [enabled = true, reason = '@Disabled is not present']
	Ans: This line is the ExecutionCondition extension API in JUnit Jupiter. The condition are enable because there is no disabled test in this program. So all test are excuted.
1.  What does Assertions.assertThrows do?
	Ans: Assertions.assertThrows will test multiple exceptions within the same test. Asserts that execution of the supplied executable throws an exception of the expectedType and returns the exception. If no exception is thrown, or if an exception of a different type is thrown, this method will fail.
1.  See TimerException and there are 3 questions
    1.  What is serialVersionUID and why do we need it? (please read on Internet)
	Ans: The serialization runtime associates with each serializable class a version number, called a serialVersionUID, which is used during deserialization to verify that the sender and receiver of a serialized object have loaded classes for that object that are compatible with respect to serialization. If the receiver has loaded a class for the object that has a different serialVersionUID than that of the corresponding sender's class, then deserialization will result in an InvalidClassException. Since serialization runtime will calculate a default serialVersionUID value for that class (if we haven't give one). So in order to get the same answer for even the same class in different JVM and compiler implementations, we need to have our own serialVersionUID. 
    2.  Why do we need to override constructors?
	Ans: Because in our output we are going to show message by calling .getMessage() and .getCause() method. Since the TimerException() constructor doesn't have a initial cause and message is null, we need to override and pass in the message or both message and cause into the constructor (based on the specific usage for the program). 
    3.  Why we did not override other Exception methods?
	Ans: Because override the constructors are based on our specific requirements and usage of the exception, for our program is not necessary to override TimerException(Throwable cause).	
1.  The Timer.java has a static block static {}, what does it do? (determine when called by debugger)
	Ans: A static initializer is invoked by the JVM and not by JUnit. If an exception is thrown within a static initializer, the test framework might not be able to catch and report the exception. For this program the static block set the configurations by read the file. If file fail to open it will catch the IOException and print the error message. 
1.  What is README.md file format how is it related to bitbucket? (https://confluence.atlassian.com/bitbucketserver/markdown-syntax-guide-776639995.html)
	Ans: .md is markdown. README.md is used to generate the html summary, and if it is in the root level, the contant of README.md will show in the Aource page of bitbucket. Within the README.md file, it has it's own syntax for doing like: attach a link to other weisites, show image, cross out a line...
1.  Why is the test failing? what do we need to change in Timer? (fix that all tests pass and describe the issue)
	Ans: The test are failing because the program throw a nullPointerExecption instead of a TimerException (if the value of timeToWait is less than zero). In order to fixed the issue, we add a condition for handling the null value.
1.  What is the actual issue here, what is the sequence of Exceptions and handlers (debug)
	Ans: The issue is we have initialize the value of timeNow to null, and cause a nullPointerException. The sequence of Exceptions are "Test Timer edgecase", "Test Timer fail", "Test Timer pass".
1.  Make a printScreen of your eclipse JUnit5 plugin run (JUnit window at the bottom panel) 
1.  Make a printScreen of your eclipse Maven test run, with console
1.  What category of Exceptions is TimerException and what is NullPointerException
	Ans: NullPointerException will throw when an application attempts to use null in a case where an object is required. TimerException is in category of runtimeException.
1.  Push the updated/fixed source code to your own repository.
