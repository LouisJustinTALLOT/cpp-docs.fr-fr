---
title: implementation_only | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- implementation_only
dev_langs:
- C++
helpviewer_keywords:
- implementation_only attribute
ms.assetid: d8cabc86-4425-45a0-9587-d57536980088
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a3a2cbf0b39dc1c5f5462ae105e2206d70a38f4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33912821"
---
# <a name="implementationonly"></a>implementation_only
**Spécifique à C++**  
  
 Supprime la génération du fichier d'en-tête .tlh (fichier d'en-tête principal).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
implementation_only  
```  
  
## <a name="remarks"></a>Notes  
 Ce fichier contient toutes les déclarations utilisées pour exposer le contenu de la bibliothèque de types. Le fichier d'en-tête .tli, avec les implémentations des fonctions membres de wrapper, sera généré et inclus dans la compilation.  
  
 Lorsque cet attribut est spécifié, le contenu de l'en-tête .tli se trouve dans le même espace de noms que celui utilisé normalement dans l'en-tête .tlh. En outre, les fonctions membres ne sont pas déclarées comme inline.  
  
 Le `implementation_only` attribut est destiné à utiliser conjointement avec la [no_implementation](../preprocessor/no-implementation.md) attribut comme un moyen de conserver les implémentations partir du fichier d’en-tête précompilé (PCH). Une instruction `#import` avec l'attribut `no_implementation` est placée dans la région source utilisée pour créer le PCH. Le PCH résultant est utilisé par plusieurs fichiers sources. Une instruction `#import` avec l'attribut `implementation_only` est ensuite utilisée hors de la zone PCH. Vous ne devez utiliser cette instruction qu'une seule fois dans l'un des fichiers sources. Cela permet de générer toutes les fonctions membres de wrapper requises sans recompilation supplémentaire pour chaque fichier source.  
  
> [!NOTE]
>  L'attribut `implementation_only` dans une instruction `#import` doit être utilisé conjointement avec une autre instruction `#import`, de la même bibliothèque de types, avec l'attribut `no_implementation`. Sinon, des erreurs du compilateur sont générées. Cela est dû au fait que les définitions de classe wrapper générées par l'instruction `#import` avec l'attribut `no_implementation` sont requises pour compiler les implémentations générées par l'attribut `implementation_only`.  
  
 **FIN spécifique à C++**  
  
## <a name="see-also"></a>Voir aussi  
 [attributs #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import (directive)](../preprocessor/hash-import-directive-cpp.md)