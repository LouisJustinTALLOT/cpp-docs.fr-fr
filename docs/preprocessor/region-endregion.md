---
title: la région, endregion | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.endregion
- endregion_CPP
- region_CPP
- vc-pragma.region
dev_langs:
- C++
helpviewer_keywords:
- pragmas, region
- pragmas, endregion
- endregion pragma
- region pragma
ms.assetid: c697f807-622f-4796-851b-68a42bbecd84
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2e360009eb9126604d4466daed2445c7dfc582d4
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808067"
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