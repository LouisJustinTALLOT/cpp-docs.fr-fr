---
title: syntaxe __based | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- based addressing
ms.assetid: a68ff750-c7fa-4c0c-8d5f-2df76e4686c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 20e1c14cd7add01f8583c24541987b2980da794a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409535"
---
# <a name="based-grammar"></a>Syntaxe __based
## <a name="microsoft-specific"></a>Section spécifique à Microsoft  
 L'adressage est utile lorsque vous avez besoin d'exercer un contrôle précis sur le segment dans lequel les objets sont alloués (données statiques et dynamiques).  
  
 Le seul type d'adressage acceptable dans les compilations 32 et 64 bits est l'adressage « basé sur un pointeur » qui définit un type contenant un déplacement 32 ou 64 bits vers une base 32 ou 64 bits ou basé sur `void`.  
  
## <a name="grammar"></a>Grammaire  
 *en fonction de modificateur de plage*:  
 **__based (***base-expression***)**   
  
 *expression de la base de*:  
 *based-variablebased-abstract-declaratorsegment-namesegment-cast*  
  
 *variable en fonction*:  
 *identifier*  
  
 *base-abstract-declarator*:  
 *abstract-declarator*  
  
 *type de base*:  
 *type-name*  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Pointeurs based](../cpp/based-pointers-cpp.md)