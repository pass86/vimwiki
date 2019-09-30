# disable logging
* Debug.logger.logEnabled = false;

# pause editor
* UnityEditor.EditorApplication.isPaused = true;

# custom property drawer
* PropertyDrawer https://docs.unity3d.com/ScriptReference/PropertyDrawer.html

# Shader
* Types
    * float 32
    * half 16 (-60000, +60000)
    * fixed 11 (-2.0, +2.0) 1/256th
* Precision of computations
    * For world space positions and texture coordinates, use float precision. 32bit
    * For everything else (vectors, HDR colors, etc.), start with half precision. Increase only if necessary. 16bit
    * For very simple operations on texture data, use fixed precision. 11bit

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

# enable unsafe in MonoDevelop
* Project>Assembly-CSharp Options>Build->General>Allow 'unsafe' code
