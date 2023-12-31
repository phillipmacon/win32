---
title: Texture2D::GatherBlue(S,float,int2,int2,int2,int2) function
description: Returns the blue components of the four texel values that would be used in a bi-linear filtering operation. | Texture2D::GatherBlue(S,float,int2,int2,int2,int2) function
ms.assetid: 0FFD3D82-E849-4C19-BEBC-85B9CCA40CA0
keywords:
- GatherBlue function HLSL
topic_type:
- apiref
api_name:
- GatherBlue
api_type:
- NA
ms.topic: reference
ms.date: 05/31/2018
api_location: 
---

# GatherBlue(S,float,int2,int2,int2,int2) function

Returns the blue components of the four texel values that would be used in a bi-linear filtering operation.

## Syntax


``` syntax
TemplateType GatherBlue(
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

[GatherBlue methods](texture2d-gatherblue.md)
</dt> </dl>








