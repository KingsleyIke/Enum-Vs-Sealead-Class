#1  What Happens When Orientation is Changed For an Activity
    The followingactivity states are called when orientaton is changed on an activity

-onPause()
-onStop()
-onDestroy()
-onCreate()
-onStart()
-onResume()

#2  The Diffrence and Similarities Between The Life Cycle of an Activity and Fragment
    Activities are where all the action happens, because they are the screens that allow the user to interact with your app.
    Activities are the foundations upon which screens and all UI elements for the app built. They encompass multiple components the user can interact with.
    
    While on the other hand a fragment is an Android component that holds part of the behavior and/or UI of an activity. As the name would suggest, fragments are       not independent entities, but are tied to a single activity. In many ways, they have functionality similar to activities.

    Activity LifeCycle                          

            onCreate()                                     
                |                                            
            onStart() <----  onRestart()                   
                |             |                                
            onResume()        |                            
                |             |                                
            onPause()         |                           
                |             |                               
            onStop()__________|                           
                |                                            
            onDestroy()          
    All the callbacks methods are associated with the lifecycle of an activity.
    
    Below is the Fragment life cycle
    Fragment LifeCycle

    onAttach()
        |
    onCreate()
        |
    onCreateView()
        |
    onViewCreated()
        |
    onStart()
        |
    onResume()
        |
    onPause()
        |
    onStop()
        |
    onDestroyView()
        |
    onDestroy()
        |
    onDetach()
