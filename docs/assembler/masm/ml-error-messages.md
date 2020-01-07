---
title: Messages d'erreur ML
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- vc.errors.ml
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), ML error messages
ms.assetid: e7e164b3-6d65-4b5b-8925-bfbebc043523
ms.openlocfilehash: 1b065433a1a6baf9bf2631aeb2f53421f8efb83b
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75312623"
---
# <a name="ml-error-messages"></a>Messages d'erreur ML

Les messages d’erreur générés par les composants MASM se répartissent en trois catégories :

- **Erreurs irrécupérables.** Ils indiquent un problème grave qui empêche l’utilitaire d’effectuer son processus normal.

- **Erreurs irrécupérables.** L’utilitaire peut terminer son processus. Si c’est le cas, son résultat n’est probablement pas celui que vous souhaitez.

- **Ceux.** Ces messages indiquent des conditions qui peuvent vous empêcher d’obtenir les résultats souhaités.

Tous les messages d’erreur prennent la forme suivante :

> *Utilitaire*: *nom de fichier* (*ligne*) : {*Error_type*} (*code*) : *message_text*

où :

\ de l' *utilitaire*
Programme qui a envoyé le message d’erreur.

*Nom de fichier*\
Fichier qui contient la condition de génération d’erreur.

\ de *ligne*
Ligne approximative dans laquelle la condition d’erreur existe.

*Error_type*\
Erreur irrécupérable, erreur ou avertissement.

*Code*\
Code d’erreur à 5 ou 6 chiffres unique.

*Message_text*\
Description brève et générale de la condition d’erreur.

## <a name="see-also"></a>Voir aussi

[Référence de Microsoft Macro Assembler](microsoft-macro-assembler-reference.md)
