---
title: Messages d’erreur ML | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
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
ms.openlocfilehash: 836daf438fa5a7f4c797b5b15ffab89720a7af98
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43675963"
---
# <a name="ml-error-messages"></a>Messages d'erreur ML

Les messages d’erreur générés par les composants MASM se répartissent en trois catégories :

- **Erreurs irrécupérables.** Ces erreurs indiquent un problème grave qui empêche l’utilitaire à partir de la fin de son processus normal.

- **Erreurs non fatales.** L’utilitaire peut terminer son processus. Le cas échéant, son résultat n’est pas susceptible d’être celle qui que vous intéresse.

- **Avertissements.** Ces messages indiquent les conditions qui peuvent vous empêcher d’obtenir les résultats souhaités.

Tous les messages d’erreur prennent la forme suivante :

> *Utilitaire*: *Filename* (*ligne*) : {*Error_type*} (*Code*) : *Message_text*

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

[Informations de référence sur Microsoft Macro Assembler](../../assembler/masm/microsoft-macro-assembler-reference.md)<br/>