---
title: region, endregion
ms.date: 10/18/2018
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
ms.openlocfilehash: c73a90aa2be83d643b74dde4645081e89da3ff73
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037924"
---
# <a name="region-endregion"></a>region, endregion

`#pragma region` vous permet de spécifier un bloc de code que vous pouvez développer ou réduire lorsque vous utilisez le [fonctionnalité mode plan](/visualstudio/ide/outlining) de l’éditeur de Code Visual Studio.

## <a name="syntax"></a>Syntaxe

```
#pragma region name
#pragma endregion comment
```

### <a name="parameters"></a>Paramètres

*commentaire*<br/>
(Facultatif) Un commentaire qui s’affiche dans l’éditeur de code.

*name*<br/>
(Facultatif) Le nom de la région.  Ce nom s'affiche dans l'éditeur de code.

## <a name="remarks"></a>Notes

`#pragma endregion` marque la fin d’un `#pragma region` bloc.

Un `#region` bloc doit se terminer par `#pragma endregion`.

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

[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)