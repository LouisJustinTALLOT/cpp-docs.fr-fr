---
title: Messages d'erreur ML
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- vc.errors.ml
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), ML error messages
ms.assetid: e7e164b3-6d65-4b5b-8925-bfbebc043523
ms.openlocfilehash: adf2c509c3d8d9110ddb757f809a4bca9199df7a
ms.sourcegitcommit: af580f3a11b19d22288424eac7ceae1bc24ab312
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66355329"
---
# <a name="ml-error-messages"></a>Messages d'erreur ML

Les messages d’erreur générés par les composants MASM se répartissent en trois catégories :

- **Erreurs irrécupérables.** Ces erreurs indiquent un problème grave qui empêche l’utilitaire à partir de la fin de son processus normal.

- **Erreurs non fatales.** L’utilitaire peut terminer son processus. Le cas échéant, son résultat n’est pas susceptible d’être celle qui que vous intéresse.

- **Avertissements.** Ces messages indiquent les conditions qui peuvent vous empêcher d’obtenir les résultats souhaités.

Tous les messages d’erreur prennent la forme suivante :

> *Utilitaire*: *Nom de fichier* (*ligne*) : {*Error_type*} (*Code*) : *Message_text*

où :

*Utilitaire*<br/>
Le programme qui a envoyé le message d’erreur.

*Nom de fichier*<br/>
Le fichier qui contient la condition de la génération d’erreur.

*Line*<br/>
La ligne approximative où la condition d’erreur existe.

*Error_type*<br/>
Irrécupérable erreur, erreur ou avertissement.

*Code*<br/>
Le code d’erreur unique 5 ou 6 chiffres.

*Message_text*<br/>
Une description courte et générale de la condition d’erreur.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur Microsoft Macro Assembler](../../assembler/masm/microsoft-macro-assembler-reference.md)
