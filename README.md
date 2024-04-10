#include "pch.h"
TEST(TestCaseName, TestName) {
	int nums1[6] = { -2,11,-4,13,-5,-2 };
	int nums2[4] = { -5,3,2,4 }; 
	int nums3[4] = { -2,4,6,4 };
	int nums4[7] = { -9,-5,-8,11,20,-2,9 };
  EXPECT_EQ(20, max_subarray_sum(nums1, 6));
  EXPECT_TRUE(true);
  EXPECT_EQ(9, max_subarray_sum(nums2, 4));
  EXPECT_TRUE(true);
  EXPECT_EQ(14, max_subarray_sum(nums3, 4));
  EXPECT_TRUE(true);
  EXPECT_EQ(38, max_subarray_sum(nums4, 7));
  EXPECT_TRUE(true);
}
// pch.cpp
#include "pch.h"
int max(int a, int b) {
    return a > b ? a : b;
}
int max_subarray_sum(int nums[], int n) {
    int max_sum = 0;
    int current_sum = 0;
    for (int i = 0; i < n; i++) {
        current_sum = max(0, current_sum + nums[i]);
        max_sum = max(max_sum, current_sum);
    }
    return max_sum;
}
// pch.h
#pragma once
#include "gtest/gtest.h"
int max(int a, int b);
int max_subarray_sum(int nums[], int n);
