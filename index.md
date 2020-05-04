## Anchor: Android app crash Locator

### Motivating Example 
#### Paradox in Fan et al's fix:

After step 3, since the onReceive() callback of both the normal BroadcastReceiver and the leaked object BroadcastReceiver would respond to the SELECT_IMAGE event. Puting a null-checker will prevent the leaked BroadcastReceiver from invoking startActivityForResult(), and allow the normal BroadcastReceiver to execute startActivityForResult(). However, since the resource leakage problem is not solved, any future functions added would still have similar problem.

#### Regression caused by Developer’s Fix ec0b92.
              
After step 3, since the onReceive() callback of both the normal BroadcastReceiver and the leaked object BroadcastReceiver would respond to the SELECT_IMAGE event. The leaked BroadcastReceivers invokes startActivityForResult(), opening the first SelectImageActivity, then the normal BroadcastReceiver invokes startActivityForResult(), causing its MainActivity to regain focus (i.e., MainActivity on top of the first SelectImageActivity), then opening a second SelectImageActivity. Resulting in the unexpected Activity Stack in Figure 4.

### Dataset in the article is accessible [here](https://github.com/Anchor-Locator/anchor).

### Anchor tool tryout is accessible [here]().
