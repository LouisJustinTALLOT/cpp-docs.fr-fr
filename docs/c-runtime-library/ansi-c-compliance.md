---
title: Conformité ANSI C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- Ansi
dev_langs:
- C++
helpviewer_keywords:
- underscores, leading
- compatibility [C++], ANSI C
- compliance with ANSI C
- conventions [C++], Microsoft extensions
- underscores
- naming conventions [C++], Microsoft library
- ANSI [C++], C standard
- Microsoft extensions naming conventions
ms.assetid: 6be271bf-eecf-491a-a928-0ee2dd60e3b9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 452c6803ea05f051727a1417aee49c3a56759141
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32387897"
---
# <a name="ansi-c-compliance"></a>Conformité ANSI C
La convention d’affectation de noms pour tous les identificateurs spécifiques à Microsoft dans le système d’exécution (par exemple, les fonctions, macros, constantes, variables et définitions de type) est compatible ANSI. Dans cette documentation, toute fonction du Runtime qui suit les normes ANSI/ISO C est indiquée comme étant compatible ANSI. Les applications compatibles ANSI doivent utiliser uniquement ces fonctions compatibles ANSI.  
  
 Les noms des fonctions spécifiques à Microsoft et les variables globales commencent par un trait de soulignement simple. Ces noms ne peuvent être remplacés que localement, dans la portée de votre code. Par exemple, lorsque vous incluez des fichiers d’en-tête de Runtime Microsoft, vous pouvez toujours substituer localement la fonction spécifique à Microsoft nommée `_open` en déclarant une variable locale du même nom. Toutefois, vous ne pouvez pas utiliser ce nom pour votre propre fonction globale ou variable globale.  
  
 Les noms de macros spécifiques et constantes manifestes spécifiques à Microsoft commencent par deux traits de soulignement, ou avec un seul trait de soulignement suivi immédiatement d’une lettre majuscule. L’étendue de ces identificateurs est absolue. Par exemple, vous ne pouvez pas utiliser l’identificateur spécifique à Microsoft **_UPPER** pour cette raison.  
  
## <a name="see-also"></a>Voir aussi  
 [Compatibilité](../c-runtime-library/compatibility.md)