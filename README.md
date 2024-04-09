#include "pch.h"
#include "CppUnitTest.h"

using namespace Microsoft::VisualStudio::CppUnitTestFramework;

namespace Test
{
	TEST_CLASS(Test)
	{
	public:
		
		TEST_METHOD(TestMethod1)
		{
		      //Assert::AreEqual(2, zitest(2, 1, 2));
			  //Assert::AreEqual(1, zitest(1, -1, 0));
			  //Assert::AreEqual(3, zitest(0, 1, 2));	
		      Assert::AreEqual(1, zitest(0, -1, 1));
		}
		int zitest(int a, int b, int c) { 
			if (a > 0 && b > 0) { // 条件1覆盖 T1，T2
				c = c / a; // 条件2覆盖 T3，T4
			}
			// 第二个条件取值组合 T1，F2，T3，F4
			if (a > 1 || c > 1) { // 条件3覆盖 T1，F2，T3
				c = c + 1; // 条件4覆盖 F4
			}
			return c;
		}
	};
}



//
// pch.cpp
//

#include "pch.h"
int zitest(int a, int b, int c) {
	if (a > 0 && b > 0) { // 条件1覆盖 T1，T2
		c = c / a; // 条件2覆盖 T3，T4
	}
	// 第二个条件取值组合 T1，F2，T3，F4
	if (a > 1 || c > 1) { // 条件3覆盖 T1，F2，T3
		c = c + 1; // 条件4覆盖 F4
	}
	return c;
}
#include "pch.h"

TEST(TestCaseName, TestName) {
  EXPECT_EQ(2, zitest(2, 1,2));
  EXPECT_TRUE(true);
  EXPECT_EQ(1, zitest(2, -1, 0));
  EXPECT_TRUE(true);
  EXPECT_EQ(3, zitest(0, 1, 2));
  EXPECT_TRUE(true);
  EXPECT_EQ(1, zitest(0, -1, 1));
  EXPECT_TRUE(true);
}
