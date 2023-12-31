---
title: Texture2D::GatherAlpha(S,float,int2,int2,int2,int2) function
description: Returns the alpha components of the four texel values that would be used in a bi-linear filtering operation. | Texture2D::GatherAlpha(S,float,int2,int2,int2,int2) function
ms.assetid: 925A5085-33CB-4DFC-B4E3-1ADA5892C13A
keywords:
- GatherAlpha function HLSL
topic_type:
- apiref
api_name:
- GatherAlpha
api_type:
- NA
ms.topic: reference
ms.date: 05/31/2018
api_location: 
---

# Texture2D::GatherAlpha(S,float,int2,int2,int2,int2) function

Returns the alpha components of the four texel values that would be used in a bi-linear filtering operation.

## Syntax


``` syntax
TemplateType GatherAlpha(
  in SamplerState S,
  in float2       Location,
  in int2         Offset1,
  in int2         Offset2,
  in int2         Offset3,
  in int2         Offset4
);
```



## Parameters

<dl> <dt>

*S* \[in\]
</dt> <dd>

Type: **SamplerState**

The zero-based sampler index.

</dd> <dt>

*Location* \[in\]
</dt> <dd>

Type: **float**

The sample coordinates (u,v).

</dd> <dt>

*Offset1* \[in\]
</dt> <dd>

Type: **int2**

The first offset component applied to the texture coordinates before sampling.

</dd> <dt>

*Offset2* \[in\]
</dt> <dd>

Type: **int2**

The second offset component applied to the texture coordinates before sampling.

</dd> <dt>

*Offset3* \[in\]
</dt> <dd>

Type: **int2**

The third offset component applied to the texture coordinates before sampling.

</dd> <dt>

*Offset4* \[in\]
</dt> <dd>

Type: **int2**

The fourth offset component applied to the texture coordinates before sampling.

</dd> </dl>

## Return value

Type: **TemplateType**

A four-component value whose type is the same as the template type.

## Remarks

The texture samples can be used for bilinear interpolation.

This function is supported for the following types of shaders:



| Vertex | Hull | Domain | Geometry | Pixel | Compute |
|--------|------|--------|----------|-------|---------|
| x      | x    | x      | x        | x     | x       |





## See also

<dl> <dt>

[GatherAlpha methods](texture2d-gatheralpha.md)
</dt> </dl>








