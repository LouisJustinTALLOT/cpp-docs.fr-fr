---
title: allocate
ms.date: 11/04/2016
f1_keywords:
- allocate_cpp
helpviewer_keywords:
- __declspec keyword [C++], allocate
- allocate __declspec keyword
ms.assetid: 67828b31-de60-4c0e-b0a6-ef3aab22641d
ms.openlocfilehash: 0bf31423cd76c838cbeffa7458bbccb89592bf43
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227619"
---
# <a name="allocate"></a>allocate

**Spécifique à Microsoft**

Le **`allocate`** spécificateur de déclaration désigne un segment de données dans lequel l’élément de données sera alloué.

## <a name="syntax"></a>Syntaxe

> **`__declspec(allocate("`***segname* **`))`** *déclarateur*

## <a name="remarks"></a>Notes

Le nom *segname* doit être déclaré à l’aide de l’un des pragmas suivants :

- [code_seg](../preprocessor/code-seg.md)

- [const_seg](../preprocessor/const-seg.md)

- [data_seg](../preprocessor/data-seg.md)

- [init_seg](../preprocessor/init-seg.md)

- [section](../preprocessor/section.md)

## <a name="example"></a>Exemple

```cpp
// allocate.cpp
#pragma section("mycode", read)
__declspec(allocate("mycode"))  int i = 0;

int main() {
}
```

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[`__declspec`](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
