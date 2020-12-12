---
description: 'En savoir plus sur les pragmas suivants : Region, endregion'
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
ms.openlocfilehash: a12305240f0c05913d16c5f26fb64661fc08e736
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167420"
---
# <a name="region-endregion-pragmas"></a>region, endregion, pragmas

`#pragma region` vous permet de spécifier un bloc de code que vous pouvez développer ou réduire lors de l’utilisation de la [fonctionnalité mode plan](/visualstudio/ide/outlining) de l’éditeur de Visual Studio code.

## <a name="syntax"></a>Syntaxe

> *nom* de la **région #pragma**\
> *commentaire* **#pragma endregion**

### <a name="parameters"></a>Paramètres

*Commentaire*\
Facultatif Commentaire à afficher dans l’éditeur de code.

*nomme*\
Facultatif Nom de la région. Ce nom s’affiche dans l’éditeur de code.

## <a name="remarks"></a>Notes

`#pragma endregion` marque la fin d’un `#pragma region` bloc.

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

[Directives Pragma et mot clé __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
