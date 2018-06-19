---
title: Messages d’erreur ML | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- vc.errors.ml
dev_langs:
- C++
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), ML error messages
ms.assetid: e7e164b3-6d65-4b5b-8925-bfbebc043523
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fbc2ae6388ad11a411850d03de421d2f6820fc03
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32057095"
---
# <a name="ml-error-messages"></a>Messages d'erreur ML
Les messages d’erreur générés par les composants MASM se répartissent en trois catégories :  
  
-   **Erreurs irrécupérables.** Celles-ci indiquent un problème grave qui empêche l’utilitaire à partir de la fin de son processus normal.  
  
-   **Erreurs récupérables.** L’utilitaire peut terminer son processus. Dans ce cas, son résultat n’est pas susceptible d’être celle qui que vous intéresse.  
  
-   **Avertissements.** Ces messages indiquent les conditions qui peuvent vous empêcher d’obtenir les résultats souhaités.  
  
 Tous les messages d’erreur prennent la forme suivante :  
  
```  
  
Utility: Filename (Line) : [Error_type} (Code): Message_text  
```  
  
 où :  
  
 `Utility`  
 Le programme qui a envoyé le message d’erreur.  
  
 *Nom de fichier*  
 Le fichier qui contient la condition de la génération d’erreur.  
  
 *Line*  
 La ligne approximative où se trouve la condition d’erreur.  
  
 *Error_type*  
 Irrécupérable erreur, erreur ou avertissement.  
  
 *Code*  
 Le code d’erreur unique 5 ou 6 chiffres.  
  
 `Message_text`  
 Description courte et générale de la condition d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur Microsoft Macro Assembler](../../assembler/masm/microsoft-macro-assembler-reference.md)