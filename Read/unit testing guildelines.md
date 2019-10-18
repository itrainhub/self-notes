## 单元测试指南

[参考文章](https://petroware.no/unittesting.html)

1. Keep unit tests small and fast

2. Unit tests should be fully automated and non-interactive
自动执行并相互没有依赖

3. Measure the tests
 测试覆盖率统计

4. Fix failing tests immediately
如果开发新功能，让旧的测试失败，那么需要警惕，应该停下来分析

5. Keep testing at unit level
测试应保持在单元水平

6. Start off simple
从简单的测试开始, 一个个简单的 test 测试最终可以建立可靠的测试系统

7. Keep tests independent
测试独立

8. Keep tests close to the class being tested.
测试文件和目标文件放一起

9. Name tests properly
好的命名: `test[what]`, such as `testSaveAa()`, `testAddListener()`, `testDeleteProperty`

10. Test public API
单元测试尽量不要取测 private 接口，这样会让测试变得冗长

11. Think black-box
按第三方接入者的思路去思考

12. Think white-box

13. Test the trivial cases too
关注细节

14. Focus on execution coverage first
execution coverage is different from actual test coverage, 执行覆盖率更加简单，可以先关注它

15. Cover boundary cases
覆盖边界情况，比如数字：测试 negatives, +0 , -0, positive, NaN, smallest, largest, infinity, etc

16. Provide a random generator
提供一个随机值生成器，这样每次测试都能使用不同的随机值去测试

17. Test each feature once
每个特性只测试一次

18. Use explicit asserts
Always prefer `assertEquals(a, b)` to `assertTrue(a == b)`

19. Provide negative tests
提供负测试

20. Design code with testing in mind

21. Don't connect to predefined external resources

22. Know the cost of testing

23. Prioritize testing

24. Write tests to reproduce bugs

25. Know the limitations
Unit tests can never prove the correctness of code
A failing test may indicate that the code contains errors, but a succeeding test doesn't prove anything at all.