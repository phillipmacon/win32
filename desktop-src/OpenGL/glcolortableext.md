---
title: glColorTableEXT function (Gl.h)
description: The glColorTableEXT function specifies the format and size of a palette for targeted paletted textures.
ms.assetid: f3d7b1a1-97a5-47ef-a0ca-5e58acb86bb4
keywords:
- glColorTableEXT function OpenGL
topic_type:
- apiref
api_name:
- glColorTableEXT
api_location:
- Gl.h
api_type:
- HeaderDef
ms.topic: reference
ms.date: 05/31/2018
---

# glColorTableEXT function

The **glColorTableEXT** function specifies the format and size of a palette for targeted paletted textures.

## Syntax


```C++
void WINAPI glColorTableEXT(
         GLenum  target,
         GLenum  internalFormat,
         GLsizei width,
         GLenum  format,
         GLenum  type,
   const GLvoid  *data
);
```



## Parameters

<dl> <dt>

*target* 
</dt> <dd>

The target texture that is to have its palette changed. Must be TEXTURE\_1D, TEXTURE\_2D, PROXY\_TEXTURE\_1D, or PROXY\_TEXTURE\_2D.

</dd> <dt>

*internalFormat* 
</dt> <dd>

The internal format and resolution of the palette. This parameter can assume one of the following symbolic values.



| Constant       | Base Format | R Bits | G Bits | B Bits | A Bits |
|----------------|-------------|--------|--------|--------|--------|
| GL\_R3\_G3\_B2 | GL\_RGB     | 3      | 3      | 2      |        |
| GL\_RGB4       | GL\_RGB     | 4      | 4      | 4      |        |
| GL\_RGB5       | GL\_RGB     | 5      | 5      | 5      |        |
| GL\_RGB8       | GL\_RGB     | 8      | 8      | 8      |        |
| GL\_RGB10      | GL\_RGB     | 10     | 10     | 10     |        |
| GL\_RGB12      | GL\_RGB     | 12     | 12     | 12     |        |
| GL\_RGB16      | GL\_RGB     | 16     | 16     | 16     |        |
| GL\_RGBA2      | GL\_RGBA    | 2      | 2      | 2      | 2      |
| GL\_RGBA4      | GL\_RGBA    | 4      | 4      | 4      | 4      |
| GL\_RGB5\_A1   | GL\_RGBA    | 5      | 5      | 5      | 1      |
| GL\_RGBA8      | GL\_RGBA    | 8      | 8      | 8      | 8      |
| GL\_RG10\_A2   | GL\_RGBA    | 10     | 10     | 10     | 2      |
| GL\_RGB12      | GL\_RGBA    | 12     | 12     | 12     | 12     |
| GL\_RGBA16     | GL\_RGBA    | 16     | 16     | 16     | 16     |



 

</dd> <dt>

*width* 
</dt> <dd>

The size of the palette. Must be 2n = 1 for some integer *n*.

</dd> <dt>

*format* 
</dt> <dd>

The format of the pixel data. The following symbolic constants are accepted.




| Value | Meaning | 
|-------|---------|
| <span id="GL_RGBA"></span><span id="gl_rgba"></span><dl><dt><strong>GL_RGBA</strong></dt></dl> | Each pixel is a group of four components in this order: red, green, blue, alpha. The RGBA format is determined in this way: <br /><ol><li>The <strong>glColorTableEXT</strong> function converts floating-point values directly to an internal format with unspecified precision. Signed integer values are mapped linearly to the internal format such that the most positive representable integer value maps to 1.0, and the most negative representable integer value maps to -1.0. Unsigned integer data is mapped similarly: the largest integer value maps to 1.0, and zero maps to 0.0.</li><li>The <strong>glColorTableEXT</strong> function multiplies the resulting color values by GL_c_SCALE and adds them to GL_c_BIAS, where <em>c</em> is RED, GREEN, BLUE, and ALPHA for the respective color components. The results are clamped to the range [0,1].</li><li>If GL_MAP_COLOR is <strong>TRUE</strong>, <strong>glColorTableEXT</strong> scales each color component by the size of lookup table GL_PIXEL_MAP_c_TO_c, then replaces the component by the value that it references in that table; <em>c</em> is R, G, B, or A, respectively.</li><li>The <strong>glColorTableEXT</strong> function converts the resulting RGBA colors to fragments by attaching the current raster position <em>z</em>-coordinate and texture coordinates to each pixel, then assigning <em>x</em> and <em>y</em> window coordinates to the <em>n</em>th fragment such that<em>x</em>? = <em>x</em><sub>r</sub> + <em>n</em> mod <em>width</em><br /><em></em>y? = <em>y</em><sub>r</sub> +<em>n / width</em><br /> where (<em>x</em><sub>r</sub> , <em>y</em><sub>r</sub> ) is the current raster position.<br /></li><li>These pixel fragments are then treated just like the fragments generated by rasterizing points, lines, or polygons. The <strong>glColorTableEXT</strong> function applies texture mapping, fog, and all the fragment operations before writing the fragments to the framebuffer.</li></ol> | 
| <span id="GL_RED"></span><span id="gl_red"></span><dl><dt><strong>GL_RED</strong></dt></dl> | Each pixel is a single red component.<br /> The <strong>glColorTableEXT</strong> function converts this component to the internal format in the same way that the red component of an RGBA pixel is, then converts it to an RGBA pixel with green and blue set to 0.0, and alpha set to 1.0. After this conversion, the pixel is treated just as if it had been read as an RGBA pixel.<br /> | 
| <span id="GL_GREEN"></span><span id="gl_green"></span><dl><dt><strong>GL_GREEN</strong></dt></dl> | Each pixel is a single green component.<br /> The <strong>glColorTableEXT</strong> function converts this component to the internal format in the same way that the green component of an RGBA pixel is, and then converts it to an RGBA pixel with red and blue set to 0.0, and alpha set to 1.0. After this conversion, the pixel is treated just as if it had been read as an RGBA pixel.<br /> | 
| <span id="GL_BLUE"></span><span id="gl_blue"></span><dl><dt><strong>GL_BLUE</strong></dt></dl> | Each pixel is a single blue component.<br /> The <strong>glColorTableEXT</strong> function converts this component to the internal format in the same way that the blue component of an RGBA pixel is, and then converts it to an RGBA pixel with red and green set to 0.0, and alpha set to 1.0. After this conversion, the pixel is treated just as if it had been read as an RGBA pixel.<br /> | 
| <span id="GL_ALPHA"></span><span id="gl_alpha"></span><dl><dt><strong>GL_ALPHA</strong></dt></dl> | Each pixel is a single alpha component.<br /> The <strong>glColorTableEXT</strong> function converts this component to the internal format in the same way that the alpha component of an RGBA pixel is, and then converts it to an RGBA pixel with red, green, and blue set to 0.0. After this conversion, the pixel is treated just as if it had been read as an RGBA pixel.<br /> | 
| <span id="GL_RGB"></span><span id="gl_rgb"></span><dl><dt><strong>GL_RGB</strong></dt></dl> | Each pixel is a group of three components in this order: red, green, blue.<br /> The <strong>glColorTableEXT</strong> function converts each component to the internal format in the same way that the red, green, and blue components of an RGBA pixel are. The color triple is converted to an RGBA pixel with alpha set to 1.0. After this conversion, the pixel is treated just as if it had been read as an RGBA pixel.<br /> | 
| <span id="GL_BGR_EXT"></span><span id="gl_bgr_ext"></span><dl><dt><strong>GL_BGR_EXT</strong></dt></dl> | Each pixel is a group of three components in this order: blue, green, red.<br /> GL_BGR_EXT provides a format that matches the memory layout of Windows device-independent bitmaps (DIBs). Thus your applications can use the same data with Windows function calls and OpenGL pixel function calls.<br /> | 
| <span id="GL_BGRA_EXT"></span><span id="gl_bgra_ext"></span><dl><dt><strong>GL_BGRA_EXT</strong></dt></dl> | Each pixel is a group of four components in this order: blue, green, red, alpha.<br /> GL_BGRA_EXT provides a format that matches the memory layout of Windows device-independent bitmaps (DIBs). Thus your applications can use the same data with Windows function calls and OpenGL pixel function calls.<br /> | 




 

</dd> <dt>

*type* 
</dt> <dd>

The data type for *data*. The following symbolic constants are accepted: GL\_UNSIGNED\_BYTE, GL\_BYTE, GL\_UNSIGNED\_SHORT, GL\_SHORT, GL\_UNSIGNED\_INT, GL\_INT, and GL\_FLOAT.

The following table summarizes the meaning of the valid constants for the *type* parameter.



| Value                                                                                                                                                                      | Meaning                                          |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------|
| <span id="GL_UNSIGNED_BYTE"></span><span id="gl_unsigned_byte"></span><dl> <dt>**GL\_UNSIGNED\_BYTE**</dt> </dl>    | Unsigned 8-bit integer<br/>                |
| <span id="GL_BYTE"></span><span id="gl_byte"></span><dl> <dt>**GL\_BYTE**</dt> </dl>                                | Signed 8-bit integer<br/>                  |
| <span id="GL_UNSIGNED_SHORT"></span><span id="gl_unsigned_short"></span><dl> <dt>**GL\_UNSIGNED\_SHORT**</dt> </dl> | Unsigned 16-bit integer<br/>               |
| <span id="GL_SHORT"></span><span id="gl_short"></span><dl> <dt>**GL\_SHORT**</dt> </dl>                             | Signed 16-bit integer<br/>                 |
| <span id="GL_UNSIGNED_INT"></span><span id="gl_unsigned_int"></span><dl> <dt>**GL\_UNSIGNED\_INT**</dt> </dl>       | Unsigned 32-bit integer<br/>               |
| <span id="GL_INT"></span><span id="gl_int"></span><dl> <dt>**GL\_INT**</dt> </dl>                                   | 32-bit integer<br/>                        |
| <span id="GL_FLOAT"></span><span id="gl_float"></span><dl> <dt>**GL\_FLOAT**</dt> </dl>                             | Single-precision floating-point value<br/> |



 

</dd> <dt>

*data* 
</dt> <dd>

A pointer to the paletted texture data. The data is treated as single pixels of a 1-D texture palette entry for a palette entry.

</dd> </dl>

## Return value

This function does not return a value.

## Error codes

The following error codes can be retrieved by the [**glGetError**](glgeterror.md) function.



| Name                                                                                                  | Meaning                                                                                                                               |
|-------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
| <dl> <dt>**GL\_INVALID\_VALUE**</dt> </dl>     | *width* was an invalid integer.<br/>                                                                                            |
| <dl> <dt>**GL\_INVALID\_ENUM**</dt> </dl>      | *target*, *internalFormat*, *format*, or *type* was not an accepted value.<br/>                                                 |
| <dl> <dt>**GL\_INVALID\_OPERATION**</dt> </dl> | The function was called between a call to [**glBegin**](glbegin.md) and the corresponding call to [**glEnd**](glend.md).<br/> |



## Remarks

Paletted textures are defined with a palette of colors and a set of image data that is composed of indexes to color entries of a palette (a color table).

The **glColorTableEXT** function specifies the texture palette of a targeted texture. It takes the *data* from memory and converts the data as if each palette entry is a single pixel of a 1-D texture. The **glColorTableEXT** function unpacks and converts the data and translates it into an internal format that matches the given *format* as closely as possible.

If a palette's *width* is greater than the range of the color indexes in the texture data, some of the palette entries are unused. If a palette's *width* is less than the range of the color indexes in the texture data, the most significant bits of the texture data are ignored and only the appropriate number of bits in the index are used when accessing the palette. When you specify a proxy *target* using PROXY\_TEXTURE\_1D or PROXY\_TEXTURE\_2D, the palette of the proxy texture is resized and its parameters are set but no data is transferred or accessed.

When the *target* parameter is GL\_PROXY\_TEXTURE\_1D or GL\_PROXY\_TEXTURE\_2D, and the implementation does not support the values specified for either *format* or *width*, **glColorTableEXT** can fail to create the requested color table. In this case, the color table is empty and all parameters retrieved will be zero. You can determine whether OpenGL supports a particular color table format and size by calling **glColorTableEXT** with a proxy target, and then calling [**glGetColorTableParameterivEXT**](glgetcolortableparameterivext.md) or [**glGetColorTableParameterfvEXT**](glgetcolortableparameterfvext.md) to determine whether the width parameter matches that set by **glColorTableEXT**. If the retrieved width is zero, the color table request by **glColorTable** failed. If the retrieved width is not zero, you can call **glColorTable** with the real target with TEXTURE\_1D or TEXTURE\_2D to set the color table.

> [!Note]  
> The **glColorTableEXT** function is an extension function that is not part of the standard OpenGL library but is part of the GL\_EXT\_paletted\_texture extension. To check whether your implementation of OpenGL supports **glColorTableEXT**, call [**glGetString**](glgetstring.md)(GL\_EXTENSIONS). If it returns GL\_EXT\_paletted\_texture, **glColorTableEXT** is supported. To obtain the function address of an extension function, call [**wglGetProcAddress**](/windows/desktop/api/wingdi/nf-wingdi-wglgetprocaddress).

 

To retrieve the actual color table data specified by the **glColorTableEXT** function, call [**glGetColorTableEXT**](glgetcolortableext.md). To retrieve the parameters, such as *width* and *format*, of the color table specified by the **glColorTableEXT** function, call the **glGetColorTableParameterivEXT** or **glGetColorTableParameterfvEXT** function.

## Requirements



| Requirement | Value |
|-------------------------------------|---------------------------------------------------------------------------------|
| Minimum supported client<br/> | Windows 2000 Professional \[desktop apps only\]<br/>                      |
| Minimum supported server<br/> | Windows 2000 Server \[desktop apps only\]<br/>                            |
| Header<br/>                   | <dl> <dt>Gl.h</dt> </dl> |



## See also

<dl> <dt>

[**glBegin**](glbegin.md)
</dt> <dt>

[**glColorSubTableEXT**](glcolorsubtableext.md)
</dt> <dt>

[**glEnd**](glend.md)
</dt> <dt>

[**glGetColorTableEXT**](glgetcolortableext.md)
</dt> <dt>

[**glGetColorTableParameterfvEXT**](glgetcolortableparameterfvext.md)
</dt> <dt>

[**glGetColorTableParameterivEXT**](glgetcolortableparameterivext.md)
</dt> <dt>

[**wglGetProcAddress**](/windows/desktop/api/wingdi/nf-wingdi-wglgetprocaddress)
</dt> </dl>

 

 





