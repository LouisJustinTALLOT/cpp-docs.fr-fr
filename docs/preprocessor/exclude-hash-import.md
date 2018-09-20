---
title: exclure (#import) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- exclude
dev_langs:
- C++
helpviewer_keywords:
- exclude attribute
ms.assetid: 0883248a-d4bf-420e-9848-807b28fa976e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5798c7515c411b9abf9d10229a6185e01bb92f7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400196"
---
# <a name="exclude-import"></a>exclude (#import)
**Spécifique à C++**  
  
Exclut des éléments des fichiers d'en-tête de bibliothèque de types en cours de création.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
exclude("Name1"[, "Name2",...])  
```  
  
### <a name="parameters"></a>Paramètres  
*Nom1*  
Premier élément à exclure.  
  
*Name2*  
Deuxième élément à exclure (si nécessaire).  
  
## <a name="remarks"></a>Notes  
 
Les bibliothèques de types peuvent inclure des définitions d'éléments définis dans les en-têtes système ou dans d'autres bibliothèques de types. Cet attribut peut prendre un nombre quelconque d’arguments, chacun étant un élément de niveau supérieur de bibliothèque de types à exclure.  
  
**FIN spécifique à C++**  
  
## <a name="see-also"></a>Voir aussi  
 
[attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directive #import](../preprocessor/hash-import-directive-cpp.md)