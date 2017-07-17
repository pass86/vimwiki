# disable logging
* Debug.logger.logEnabled = false;

# pause editor
* UnityEditor.EditorApplication.isPaused = true;

# custom property drawer
* PropertyDrawer https://docs.unity3d.com/ScriptReference/PropertyDrawer.html

# shader
* types
    * float 32
    * half 16 (-60000, +60000)
    * fixed 11 (-2.0, +2.0) 1/256th

# winding order
* clockwise front visible

# texture
* (0, 0) at lower left corner

# editor useful
* GUILayout.Button
* EditorGUILayout.ObjectField
* EditorWindow.GetWindow(typeof(Foo), true, "Foo");

# native
* http://www.mono-project.com/docs/advanced/pinvoke/
* never pass classes or structures containing members of reference type (classes) to unmanaged code

# apk size
* FAT(ARMv7+x86) - ARMv7 = 9.9M