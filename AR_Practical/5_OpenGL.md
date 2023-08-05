# OpenGL

#Lighting #Phong
## General

- OpenGL is a state Machine, you set something *once* and it *stays* until you change it
	  → glColor4f() until you set a new Color
	  → glTranslatef() until you change the current matrix
- OpenGL works with a stack, you always have a current matrix you are working with and a stack which you can push/pop
	  → OpenGL actually has 3 Stacks (there can be an additional Color Stack but it is not default)
- Operations are applied to the current Matrix 

## Stack / Matrix Modes

```cpp
void glMatrixMode(GLenum mode);

GLenum mode {
    GL_MODELVIEW, //Applies subsequent matrix operations to the modelview matrix stack. 
	GL_PROJECTION, //Applies subsequent matrix operations to the projection matrix stack. 
	GL_TEXTURE, //Applies subsequent matrix operations to the texture matrix stack. 
	GL_COLOR //Applies subsequent matrix operations to the color matrix stack. 
};
```

- Operations are applied to the **top Matrix** of the current stack
- Initially stack is empty and current matrix is the identity matrix
- Applying transformations update the current Matrix consecutively

```cpp
glPushMatrix(); //Duplicates current Matrix and pushes stack down by 1
glPopMatrix(); //Pops current Matrix Stack, replacing current with one below

glLoadIdentity(); //replaces current matrix with identity Matrix
glLoadMatrix(const GLfloat * m); //replaces current matrix with the specified matrix
```

## Functions

```cpp
glTranslatef(float x, float y, float z);
	// specify the x y z component of a translation vector

glRotatef(float angle, float x, float y, float z);
	// specifies a rotation of angle degrees around the vector xyz

glScalef(float x, float y, float z);
	// specify scale factors along the x, y, and z axes, respectively.

glColor4f(float r, float g, float b, float alpha)
	//specify new red, green, blue and alpha values for the current color
```

## Scope of OpenGL Calls

- Draw calls use the **current** matrix for their drawing → this means any transformations have to be specified beforehand
- Draw calls do **not** reset the current matrix (!)
- glColor is special and stays until you specify a new color
- Transformations are relevant until the current Matrix or Matrix mode is changed

## Lighting / Phong-Rendering

- OpenGL considers lighting to be divided into four independent components: emissive, ambient, diffuse and specular
	  → All four components are computed independently and then added together to render a scene with the **Phong-Lighting** Model (Model = Ambient + Diffuse + Specular)
### Emissive
- this is the special case of OpenGL lighting, if a material has an *emissive* color it simulates light originating from this object
- this is unaffected by any lightsources
- **but** it also does not add light to a scene

### Ambient
- this is the general scattered light level of a scene, it typically results in an image without any shading, just flat colours
### Diffuse
- the effect of directed light sources that scatter through the creases and crevices of our object
	  → this is typically what you would see as adding shadows to your scene
### Specular
- The Highlights of shiny material, where the roughness is low and bounces of the surface
	  → highlights are the shiny parts c:


→ combining our lighting model results in a wonderfully lit object ([Source Wikimedia](https://commons.wikimedia.org/wiki/File:Blinn_phong_comparison.png))

![[phong_rendering.png]]

