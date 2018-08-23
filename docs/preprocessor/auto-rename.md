---
title: auto_rename | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- auto_rename
dev_langs:
- C++
helpviewer_keywords:
- auto_rename attribute
ms.assetid: 1075f3ab-f6fc-4e04-8e22-ebe02695a567
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 70049daf514659a9ae525e1fca40152df4ab382a
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2018
ms.locfileid: "42540564"
---
# <a name="autorename"></a>auto_rename
**Spécifique à C++**  
  
Renomme des mots réservés C++ en ajoutant deux traits de soulignement (__) au nom de variable pour résoudre les conflits potentiels entre les noms.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
auto_rename  
```  
  
## <a name="remarks"></a>Notes 

Cet attribut est utilisé lors de l'importation d'une bibliothèque de types qui utilise un ou plusieurs mots réservés C++ (mots clés ou macros) comme noms de variables.  
  
 **FIN spécifique à C++**  
  
## <a name="see-also"></a>Voir aussi 

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)   
[directive #import](../preprocessor/hash-import-directive-cpp.md)