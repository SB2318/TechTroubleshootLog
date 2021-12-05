It is a common but important problem in the case of development that any method is suddenly deprecated. Newbie developers tend to be more suffer in this mess.
Let's see how profitable this solution can be.

<a href="https://www.truiton.com/2013/06/android-fragmentpageradapter-vs-fragmentstatepageradapter/">FragmentStatePagerAdapter</a> should be used when we have to use dynamic fragments, like fragments with widgets, as their data could be stored in the savedInstanceState. Also, it won't affect the performance even if there are a large number of fragments.

`public abstract class FragmentStatePagerAdapter extends PagerAdapter`

You can see it's implementation <a href="https://developer.android.com/reference/androidx/fragment/app/FragmentStatePagerAdapter#summary"> here.</a>

Now the problem is this is currently a deprecated method.

For this, we have three alternatives.

<h2><b>First,</b></h2>
<br>

Use `FragmentStatePagerAdapter` with `BEHAVIOR_RESUME_ONLY_CURRENT_FRAGMENT`


```
public static class MyAdapter extends FragmentStatePagerAdapter {
        public MyAdapter(FragmentManager fm) {
            super(fm, BEHAVIOR_RESUME_ONLY_CURRENT_FRAGMENT);
        }

        @Override
        public int getCount() {
            return NUM_ITEMS;
        }

        @Override
        public Fragment getItem(int position) {
            return ArrayListFragment.newInstance(position);
        }
    }

```
<h2><b>Second,</b></h2>
<br>

We can use the parent class <a href="https://developer.android.com/reference/androidx/viewpager/widget/PagerAdapter">PagerAdapter.</a> 

I want to give the implementation of the PagerAdapter a little different. Because the purpose of my repository is to find a solution and to help Beginner Android developers. **Because a lot of times we don't know what to look for.**
I shared here the solution that helped me a lot, <a href="https://camposha.info/android-examples/android-pageradapter/#gsc.tab=0">click here.</a>

<h2><b>Third, using FragmentStateAdapter</b> </h2>
<br>

We can use <a href="https://developer.android.com/training/animation/vp2-migration">ViewPager2</a> instead of using ViewPager</a>.
<a href="https://github.com/SB2318/kotlin-java-project-error/blob/main/android/issue2/associate.md">Click here</a> to see an implementation that can be helpful.

<h3>Why can't we implement FragmentStateAdapter with ViewPager?</h3>

----
## To be continue





