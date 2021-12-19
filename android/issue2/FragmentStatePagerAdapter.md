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

Both the ViewPager and ViewPager2 have a `setAdapter()` method, with the help of which we set the adapter into ViewPager.

`public abstract class FragmentStateAdapter extends Adapter<FragmentViewHolder> implements StatefulAdapter`

`public abstract class PagerAdapter extends Object`

Here we see FragmentStateAdapter extends Adapter class.But PagerAdapter class extends the Object class.So,we can't  able to establish a stable relationship between the two of them.
But  as an argument,`setAdapter()` method of ViewPager takes an instance of PagerAdapter class.

---

![viewpager](https://user-images.githubusercontent.com/87614560/146673715-20c9e794-42e1-49d9-9a69-466e4f0c6b30.png)

---

On the other hand, the `setAdapter()` method of ViewPager2 takes an Adapter class instance as an argument.

---

![viewpager2](https://user-images.githubusercontent.com/87614560/146673723-0e3bd278-355c-4cb2-a1d9-fb11e3e2571b.png)

---

FragmentStateAdapter is a child class of Adapter class.
For this reason, we can easily use it with ViewPager2. But we can't use it with ViewPager.






