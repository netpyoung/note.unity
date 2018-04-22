Unity Shaders and Effects Cookbook
http://www.amazon.com/Unity-Shaders-Effects-Cookbook-Lammers/dp/1849695083



C:\Program Files (x86)\Unity\Editor\Data\CGIncludes



http://unitygems.com/noobshader1
http://unitygems.com/noobs-guide-shaders-2/
http://unitygems.com/noobs-guide-shaders-3-realistic-snow/
http://unitygems.com/noobs-guide-shaders-4-toon-shading-basic/
http://unitygems.com/noobs-guide-shaders-5-bumped-diffuse-shader/
http://unitygems.com/noobs-guide-shaders-6-toon-shader/





```shaderlab
http://docs.unity3d.com/Manual/SL-Shader.html

Shader <shader-name> {

	http://docs.unity3d.com/Manual/SL-Properties.html
    Properties {
        _PropertyName ("displayed name", <property-type>) = <property-default-value>
    }
	
	
	
	http://docs.unity3d.com/Manual/SL-SubShader.html
    Subshader {
	
		http://docs.unity3d.com/Manual/SL-SubshaderTags.html
		[Tags {<tag-name> = <tag-value>}]
		
		
		
		http://docs.unity3d.com/Manual/SL-ShaderLOD.html
		[LOD <lod-number>]
			
		[
			http://docs.unity3d.com/Manual/SL-UsePass.html
			UsePass "Shader/Name"
			
			
			http://docs.unity3d.com/Manual/SL-GrabPass.html
			GrabPass {} || GrabPass { "TextureName" }
			
		]
		
		
		
		http://docs.unity3d.com/Manual/SL-Pass.html
		Pass {
			Name "PassName"

			
			[
				Tags
			
				http://docs.unity3d.com/Manual/SL-Material.html
			    Material {Material Block}
				Lighting On | Off
				Color Color-value
				ColorMask RGB | A | 0 | any combination of R, G, B, A
				SeparateSpecular On | Off
				ColorMaterial AmbientAndDiffuse | Emission
				
				
				http://docs.unity3d.com/Manual/SL-CullAndDepth.html
				Cull Back | Front | Off
			    ZTest (Less | Greater | LEqual | GEqual | Equal | NotEqual | Always)
				Offset OffsetFactor, OffsetUnits
				

				http://docs.unity3d.com/Manual/SL-Fog.html
				Fog {Fog Block}
				
				
				http://docs.unity3d.com/Manual/SL-AlphaTest.html
				AlphaTest (Less | Greater | LEqual | GEqual | Equal | NotEqual | Always) CutoffValue

				
				http://docs.unity3d.com/Manual/SL-Blend.html
				Blend SourceBlendMode DestBlendMode
			]
			
			
			[TextureSetup]
		}
		
		
		http://docs.unity3d.com/Manual/SL-Other.html
		Category {
		}		
	}
	
	
	
	http://docs.unity3d.com/Manual/SL-Fallback.html
	Fallback Off || Fallback <other-shader-name>
	
	
	
	http://docs.unity3d.com/Manual/SL-CustomEditor.html
	http://docs.unity3d.com/Manual/SL-CustomMaterialEditors.html
	CustomEditor <custom-editor-class-name>
	
}
```





====================================================================



# Surface
http://docs.unity3d.com/Manual/SL-SurfaceShaders.html

if your shader needs to be affected by lights and shadows


struct SurfaceOutput {
    half3 Albedo;		//The color of the pixel
    half3 Normal;		//The normal of the pixel
    half3 Emission;		//The emissive color of the pixel
    half Specular;		//Specular power of the pixel
    half Gloss;			//Gloss intensity of the pixel
    half Alpha;			//Alpha value for the pixel
};




# Vertex


# Fragment


if your shader doesn't need to interact with lighting, 
if you need some very exotic effects that the surface shaders can't handle. 


# Fixed Function Shaders


Writing vertex and fragment shaders: http://docs.unity3d.com/Manual/SL-ShaderPrograms.html





====================================================================



## <property-type>
 * Color
	- (r, g, b, a)
 * 2D - the value is a power of 2 sized texture that can be sampled by the program for a particular pixel based on the UVs of the model 
	- "", "white", "black", "gray", "bump"
 * Rect - the value is a texture that is not a power of 2 size
	- "", "white", "black", "gray", "bump"
 * Cube - the value is a 3D cube map texture used for reflections, this can be sampled by the program for a particular pixel
	- "", "white", "black", "gray", "bump"
 * Range(min, max) - the value is a floating point between a minimum and maximum value
 * Float - the value is a floating point number with any value
 * Vector - the value is a 4 dimensional vector
	- (x, y, z, w)


	

# TODO

http://docs.unity3d.com/Manual/SL-AdvancedTopics.html



Tags

"Queue"
Background	1000	(ex. skyboxes)
Geometry	2000	(default)
AlphaTest	2450
Transparent	3000
Overlay		4000	(ex. lens flares)




# Shader Program

http://docs.unity3d.com/Manual/SL-ShaderPrograms.html


```
#pragma surface surf Lambert

- shader : `surface`
- output : `surf`
- light model : `lambert`
```








shaderfx




https://developer.nvidia.com/cg-toolkit
