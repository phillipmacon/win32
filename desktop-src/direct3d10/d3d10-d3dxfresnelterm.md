---
description: D3DXFresnelTerm function (D3DX10Math.h) - Calculate the Fresnel term.
ms.assetid: eaa2e5ea-9b6f-4216-8b48-7be74501124d
title: D3DXFresnelTerm function (D3DX10Math.h)
ms.topic: reference
ms.date: 05/31/2018
topic_type:
- APIRef
- kbSyntax
api_name:
- D3DXFresnelTerm
api_type:
- LibDef
api_location:
- D3DX10.lib
- D3DX10.dll
---

# D3DXFresnelTerm function (D3DX10Math.h)

> [!Note]
> The D3DX utility library is deprecated. We recommend that you use [DirectXMath](../dxmath/pg-xnamath-migration-d3dx.md) instead.

Calculate the Fresnel term.

## Syntax


```C++
FLOAT D3DXFresnelTerm(
  _In_ FLOAT CosTheta,
  _In_ FLOAT RefractionIndex
);
```



## Parameters

<dl> <dt>

*CosTheta* \[in\]
</dt> <dd>

Type: **[**FLOAT**](../winprog/windows-data-types.md)**

The value must be between 0 and 1.

</dd> <dt>

*RefractionIndex* \[in\]
</dt> <dd>

Type: **[**FLOAT**](../winprog/windows-data-types.md)**

The refraction index of a material. The value must be greater than 1.

</dd> </dl>

## Return value

Type: **[**FLOAT**](../winprog/windows-data-types.md)**

This function returns the Fresnel term for unpolarized light. CosTheta is the cosine of the incident angle.

## Remarks

To find the Fresnel term (F):

If A is angle of incidence and B is the angle of refraction, then


```
F = 0.5 * [tan2(A - B) / tan2(A + B) + sin2(A - B) / sin2(A + B)]
  = 0.5 * sin2(A - B) / sin2(A + B) * [cos2(A + B) / cos2(A - B) + 1]

Let r   = sina(A) / sin(B)      (the relative refractive index)
Let c   = cos(A)
Let g   = (r2 + c2 - 1)1/2
```



Then, expanding using the trig identities and simplifying, you get:


```
F = 0.5 * (g + c)2 / (g - c)2 * ([c(g + c) - 1]2 / [c(g - c) + 1]2 + 1)
```



## Requirements



| Requirement | Value |
|--------------------|-----------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>D3DX10Math.h</dt> </dl> |
| Library<br/> | <dl> <dt>D3DX10.lib</dt> </dl>   |



## See also

<dl> <dt>

[Math Functions](d3d10-graphics-reference-d3dx10-functions-math.md)
</dt> </dl>

 

 
