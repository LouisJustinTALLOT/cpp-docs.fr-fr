---
title: "Type pour les littéraux de chaîne | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- string literals, type
- types [C], string literals
ms.assetid: f50a28af-20c1-4440-bdc6-564c86a309c8
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2342777bfd2b1a039e68766e8dfe00ac2fa2f932
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="type-for-string-literals"></a>Type pour les littéraux de chaîne
Les littéraux de chaîne ont un tableau de type `char` (autrement dit, **char[ ]**). (Les chaînes à caractères larges ont un tableau de type `wchar_t` (autrement dit, **wchar_t[ ]**).) Cela signifie qu'une chaîne est un tableau avec des éléments de type `char`. Le nombre d'éléments du tableau est égal au nombre de caractères dans la chaîne plus un pour le caractère null de fin.  
  
## <a name="see-also"></a>Voir aussi  
 [Littéraux de chaîne C](../c-language/c-string-literals.md)