---
title: la région, endregion | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 9e6ec22be873dcec06f224913eb905a2779e4efd
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2018
ms.locfileid: "42545746"
---
# <a name="region-endregion"></a>region, endregion
`#pragma region` vous permet de spécifier un bloc de code que vous pouvez développer ou réduire lorsque vous utilisez le [fonctionnalité mode plan](/visualstudio/ide/outlining) de l’éditeur de Code Visual Studio.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma region name  
#pragma endregion comment  
```  
  
### <a name="parameters"></a>Paramètres  
*commentaire* (facultatif)  
Commentaire qui s'affiche dans l'éditeur de code.  
  
*name* (facultatif)  
Nom de la région.  Ce nom s'affiche dans l'éditeur de code.  
  
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