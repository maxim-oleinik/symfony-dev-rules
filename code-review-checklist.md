[Чеклист взят отсюда](http://joseantony.com/2010/12/04/php-code-review-checklist/)

PHP Code review checklist
=========================

I love to do code reviews because it give me chance to see how other people write code and improve mine also. I have seen many people who are afraid of doing code review. Which made think of creating a code review checklist for php. Please note this is not full checklist for code review and following all the conditions in this will not end up in a great code. But following this will end up in  code that can be maintained by others in the later stage of code development.

1. No syntax/runtime errors and warnings in the code
2. No deprecated functions in  the code – You can get the list of deprecated function in php3 from the url http://nl.php.net/manual/en/migration53.deprecated.php (Thanks for Frank for sharing me this link)
3. There should be an explanation for any code that is commented out. “Dead Code” should be removed. If it is a temporary hack, it should be identified as such.
4. Check if code has file/class/function level comments.  And each of this comments should explain what the file/class/function is doing inside it.
5. Check that each function is doing only a single thing. That is never function named createCustomer should delete the existing customer and create it again
6. A method should not be larger than 40 lines of code. The basic idea is always a function should  be viewable in single screen with out scrolling.
7. Always try to initialize the variable before using that in a function.
8. No public class attributes.
9. Always try to use constants in the left hand side of the comparison. That is instead of doing if ($variable == 2) always use if (2 == $variable) because this will help to identify the errors in the earlier stage of development even if we miss and “=” from  that statement
10. Never ever mix the php code and template (view). In ideal condition a view should not contain any logic.
11. Always try using single quote ( ‘ ) when working with the php string because it has a minor performance improvement when compared to the double quotes ( ” ). The difference come from the factor that ( ” ) can be used to build a string with variables inside it.
12. There should be no catch blocks which catches an exception  and throw that again. This is because exception can bubble up to the top function call stack automatically.
13. Never ever throw a general  exception with a custom message. Always try to create a custom exception so that all the other code can handle this situation correctly.
14. Make sure that the top most code handles all the exceptions correctly shows correct / understandable error messages to the user
15. In the case of a system crash never ever put up the error information that expose the internal  behavior of the system.
16. Make sure that a proper and uniform coding standard is followed through out the files. I have seen many projects where people mix up the coding style. For php I usually use PHP Code Sniffer for validating the coding style.
17. Try using the tools like PMD to identify possible bug, dead code, over complicated expression, suboptimal code, duplicate code.
18. No magic numbers. There should be no magic numbers like 6,10 etc… any numbers like this should be define as a constant. And Constants should be well commented about the purpose.
19. Never allow bad code with some good comments
20. Always try to have unit test for the new piece of code. In ideal condition we should have 100% unit test coverage
21. Never allow unit test that are written to show 100% coverage and doesn’t do anything that unit test is supposed to do. I have seen unit test code which just call the function to get 100% coverage and doesn’t have any assertions.
22. Always commit /Rollback database transaction at the earliest. Keep the database transaction short as possible.
23. Always have an eye on the recursive functions.
24. Optimizations may often make code harder to read and more likely to contain bugs. Such optimizations should be avoided unless a need has been identified. Has the code been profiled? Check if any over optimization has led to functionality disappearing.
25. As a reviewer, you should understand the code. If you don’t, the review may not be complete, or the code may not be well commented.
26. Lastly, when executed, the code should do what it is supposed to.
