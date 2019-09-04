---
title: region, endregion, pragmas
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.endregion
- endregion_CPP
- region_CPP
- vc-pragma.region
helpviewer_keywords:
- pragmas, region
- pragmas, endregion
- endregion pragma
- region pragma
ms.assetid: c697f807-622f-4796-851b-68a42bbecd84
ms.openlocfilehash: 4a01e04582ac81d678aa0702945c62ee974a4428
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222379"
---
# <a name="region-endregion-pragmas"></a>region, endregion, pragmas

`#pragma region`vous permet de spécifier un bloc de code que vous pouvez développer ou réduire lors de l’utilisation de la [fonctionnalité mode plan](/visualstudio/ide/outlining) de l’éditeur de Visual Studio code.

## <a name="syntax"></a>Syntaxe

> **#pragma la région** *nom*\
> **#pragma endregion** *Commentaire*

### <a name="parameters"></a>Paramètres

*Commentaire*\
Facultatif Commentaire à afficher dans l’éditeur de code.

*nomme*\
Facultatif Nom de la région. Ce nom s’affiche dans l’éditeur de code.

## <a name="remarks"></a>Notes

`#pragma endregion`marque la fin d’un `#pragma region` bloc.

Un `#region` bloc doit se terminer par une `#pragma endregion` directive.

## <a name="example"></a>Exemple

```cpp
// pragma_directives_region.cpp
#pragma region Region_1
void Test() {}
void Test2() {}
void Test3() {}
#pragma endregion Region_1

int main() {}
```

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
