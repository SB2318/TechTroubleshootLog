It is a common but important problem in the case of development that any method is suddenly deprecated. Newbie developers tend to be more suffer in this mess.
Let's see how profitable this solution can be.

<a href="https://www.truiton.com/2013/06/android-fragmentpageradapter-vs-fragmentstatepageradapter/">FragmentStatePagerAdapter</a> should be used when we have to use dynamic fragments, like fragments with widgets, as their data could be stored in the savedInstanceState. Also, it won't affect the performance even if there are a large number of fragments.

`public abstract class FragmentStatePagerAdapter extends PagerAdapter`

You can see it's implementation <a href="https://developer.android.com/reference/androidx/fragment/app/FragmentStatePagerAdapter#summary"> here.</a>

Now the problem is this is currently a deprecated method.

For this, we have two alternatives.

**First,** We can use the parent class <a href="https://developer.android.com/reference/androidx/viewpager/widget/PagerAdapter">PagerAdapter.</a>

**Second,** We can use <a href="https://developer.android.com/training/animation/vp2-migration">ViewPager2</a> instead of using ViewPager</a>.


**But here's what I want to explain,**

 * How do we do that?
 * What's the difference generated with our existing code?
 * In the second case, why we could not do the same job with the help of ViewPager.
 
 <h2>Using PagerAdapter:</h2>
 ---
 <h2>To be Continue...</h2>

