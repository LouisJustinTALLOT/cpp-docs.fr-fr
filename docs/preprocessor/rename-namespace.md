---
title: rename_namespace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- rename_namespace
dev_langs:
- C++
helpviewer_keywords:
- rename_namespace attribute
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7608255b5369443ce1045f896b776cb283fdb1cb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46411857"
---
# <a name="renamenamespace"></a>rename_namespace
**Spécifique à C++**  
  
Renomme l'espace de noms qui contient le contenu de la bibliothèque de types.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
rename_namespace("NewName")  
```  
  
### <a name="parameters"></a>Paramètres  
*NewName*  
Nom du nouvel espace de noms.  
  
## <a name="remarks"></a>Notes  
 
Il accepte un seul argument, *NewName*, qui spécifie le nouveau nom de l’espace de noms.  
  
Pour supprimer l’espace de noms, utilisez le [no_namespace](../preprocessor/no-namespace.md) attribut à la place.  
  
**FIN spécifique à C++**  
  
## <a name="see-also"></a>Voir aussi  
 
[attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directive #import](../preprocessor/hash-import-directive-cpp.md)