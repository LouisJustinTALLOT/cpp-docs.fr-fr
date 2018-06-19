---
title: execution_character_set | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- execution_character_set
- vc-pragma.execution_character_set
dev_langs:
- C++
helpviewer_keywords:
- pragma execution_character_set
ms.assetid: 32248cbc-7c92-4dca-8442-230c052b53ad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2b6cb84ae6ffebda3dd335bc001463e2d8579f99
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33850292"
---
# <a name="executioncharacterset"></a>execution_character_set
Spécifie le jeu de caractères d’exécution utilisé pour les littéraux de chaîne et de caractère. Cette directive n’est pas nécessaire pour les littéraux marqués avec le préfixe u8.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma execution_character_set("target")  
```  
  
#### <a name="parameters"></a>Paramètres  
 `target`  
 Spécifie le jeu de caractères cible d’exécution. Actuellement, l’exécution de la cible uniquement définie pris en charge est « utf-8 ».  
  
## <a name="remarks"></a>Notes  
 Cette directive de compilateur est obsolète à partir de Visual Studio 2015 Update 2. Nous vous recommandons d’utiliser le **/execution-charset:utf-8** ou **/UTF-8** options du compilateur ainsi que d’à l’aide de la `u8` préfixe sur étroit caractère littéraux et de chaîne qui contiennent des étendues caractères. Pour plus d’informations sur la `u8` du préfixe URI, consultez [littéraux de chaîne et caractère](../cpp/string-and-character-literals-cpp.md). Pour plus d’informations sur les options du compilateur, consultez [/Execution-CharSet (définir l’exécution du jeu de caractères)](../build/reference/execution-charset-set-execution-character-set.md) et [/UTF-8 (définir la Source et exécutable jeux au format UTF-8 de caractères)](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md).  
  
 Le `#pragma execution_character_set("utf-8")` directive indique au compilateur pour encoder des caractères étroits et les littéraux de chaîne étroits dans votre code source en UTF-8 dans le fichier exécutable. Cet encodage de sortie est indépendant de l’encodage du fichier source utilisé.  
  
 Par défaut, le compilateur encode les caractères étroits et les chaînes étroites à l’aide de la page de codes actuelle en tant que le jeu de caractères d’exécution. Cela signifie que les caractères Unicode ou DBCS dans un littéral qui sont en dehors de la plage de la page de codes actuelle sont convertis en caractère de remplacement par défaut dans la sortie. Les caractères Unicode et DBCS sont tronquées à leur octet de poids faible. Cela est certainement pas à vos attentes. Vous pouvez spécifier l’encodage UTF-8 pour les littéraux dans le fichier source en utilisant un `u8` préfixe. Le compilateur passe ces chaînes encodées UTF-8 à la sortie inchangée. Les littéraux de caractère étroit précédées u8 doivent tenir dans un seul octet, ou elles sont tronquées en sortie.  
  
 Par défaut, Visual Studio utilise la page de codes actuelle en tant que le jeu de caractères source utilisé pour interpréter votre code source pour la sortie. Lors de la lecture d’un fichier dans Visual Studio l’interprète en fonction de la page de codes actuelle, sauf si la valeur de la page de codes du fichier, ou, sauf si une marque d’ordre d’octet (BOM) ou des caractères UTF-16 sont détectés au début du fichier. UTF-8 ne peuvent pas être définis en tant que la page de codes actuelle, lorsque la détection automatique rencontre des fichiers sources encodés en UTF-8 sans une nomenclature, Visual Studio suppose qu’ils sont encodés à l’aide de la page de codes actuelle. Caractères dans le fichier source qui sont en dehors de la plage de l’objet ou automatiquement détectées page de codes peut entraîner des erreurs et avertissements du compilateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Directives pragma et mot clé _pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
 [/ EXECUTION-CharSet (définir l’exécution du jeu de caractères)](../build/reference/execution-charset-set-execution-character-set.md)   
 [/utf-8 (Définir les jeux de caractères sources et exécutables sur UTF-8)](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)