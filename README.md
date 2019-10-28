# LeakEditText
EditText leaking context

```
HeapAnalysisSuccess(heapDumpFile=/data/user/0/com.colevit.leakyeditText/files/leakcanary/2019-10-28_19-32-19_793.hprof, createdAtTimeMillis=1572271412312, analysisDurationMillis=70469, applicationLeaks=[], libraryLeaks=[LibraryLeak(className=com.colevit.leakyeditText.MainActivity, leakTrace=
    ┬
    ├─ android.view.inputmethod.InputMethodManager
    │    Leaking: NO (InputMethodManager↓ is not leaking and a class is never leaking)
    │    GC Root: System class
    │    ↓ static InputMethodManager.sInstance
    ├─ android.view.inputmethod.InputMethodManager
    │    Leaking: NO (InputMethodManager is a singleton)
    │    ↓ InputMethodManager.mNextServedView
    │                         ~~~~~~~~~~~~~~~
    ├─ androidx.appcompat.widget.AppCompatEditText
    │    Leaking: YES (View.mContext references a destroyed activity)
    │    mContext instance of com.colevit.leakyeditText.MainActivity with mDestroyed = true
    │    View#mParent is set
    │    View#mAttachInfo is null (view detached)
    │    View.mWindowAttachCount = 1
    │    ↓ AppCompatEditText.mContext
    ╰→ com.colevit.leakyeditText.MainActivity
    ​     Leaking: YES (AppCompatEditText↑ is leaking and Activity#mDestroyed is true and ObjectWatcher was watching this)
    ​     key = 82de36fa-7175-4ab7-bc4a-11f448628ecc
    ​     watchDurationMillis = 5305
    ​     retainedDurationMillis = 260
    , retainedHeapByteSize=54315, pattern=instance field android.view.inputmethod.InputMethodManager#mNextServedView, description=When we detach a view that receives keyboard input, the InputMethodManager leaks a reference to it until a new view asks for keyboard input. Tracked here: https://code.google.com/p/android/issues/detail?id=171190 Hack: https://gist.github.com/pyricau/4df64341cc978a7de414), LibraryLeak(className=androidx.constraintlayout.widget.ConstraintLayout, leakTrace=
    ┬
    ├─ android.view.inputmethod.InputMethodManager
    │    Leaking: NO (InputMethodManager↓ is not leaking and a class is never leaking)
    │    GC Root: System class
    │    ↓ static InputMethodManager.sInstance
    ├─ android.view.inputmethod.InputMethodManager
    │    Leaking: NO (InputMethodManager is a singleton)
    │    ↓ InputMethodManager.mNextServedView
    │                         ~~~~~~~~~~~~~~~
    ├─ androidx.appcompat.widget.AppCompatEditText
    │    Leaking: YES (View.mContext references a destroyed activity)
    │    mContext instance of com.colevit.leakyeditText.MainActivity with mDestroyed = true
    │    View#mParent is set
    │    View#mAttachInfo is null (view detached)
    │    View.mWindowAttachCount = 1
    │    ↓ AppCompatEditText.mParent
    ╰→ androidx.constraintlayout.widget.ConstraintLayout
    ​     Leaking: YES (AppCompatEditText↑ is leaking and View.mContext references a destroyed activity and ObjectWatcher was watching this)
    ​     mContext instance of com.colevit.leakyeditText.MainActivity with mDestroyed = true
    ​     View#mParent is null
    ​     View#mAttachInfo is null (view detached)
    ​     View.mWindowAttachCount = 1
    ​     key = 468fc6a9-b089-4abb-a86a-e311c120678d
    ​     watchDurationMillis = 5292
    ​     retainedDurationMillis = 260
    , retainedHeapByteSize=1545, pattern=instance field android.view.inputmethod.InputMethodManager#mNextServedView, description=When we detach a view that receives keyboard input, the InputMethodManager leaks a reference to it until a new view asks for keyboard input. Tracked here: https://code.google.com/p/android/issues/detail?id=171190 Hack: https://gist.github.com/pyricau/4df64341cc978a7de414)])
    
   ```
