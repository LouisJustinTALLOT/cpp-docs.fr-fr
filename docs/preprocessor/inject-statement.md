---
title: inject_statement | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- inject_statement
dev_langs:
- C++
helpviewer_keywords:
- inject_statement attribute
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 115f5b3d7012ae3e9073d81e0c1005dcb513e045
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33849338"
---
# <a name="injectstatement"></a>inject_statement
**Spécifique à C++**  
  
 Insère son argument en tant que texte source dans l’en-tête de bibliothèque de types.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
inject_statement("source_text")  
```  
  
#### <a name="parameters"></a>Paramètres  
 `source_text`  
 Texte source à insérer dans le fichier d'en-tête de bibliothèque de types.  
  
## <a name="remarks"></a>Notes  
 Le texte est placé au début de la déclaration d'espace de noms qui encapsule le contenu de la bibliothèque de types dans le fichier d'en-tête.  
  
 **FIN spécifique à C++**  
  
## <a name="see-also"></a>Voir aussi  
 [attributs #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import (directive)](../preprocessor/hash-import-directive-cpp.md)