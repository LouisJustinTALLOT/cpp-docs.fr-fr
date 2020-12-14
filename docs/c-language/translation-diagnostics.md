---
description: 'En savoir plus sur : traduction : Diagnostics'
title: 'Traduction : Diagnostics'
ms.date: 11/04/2016
ms.assetid: 3730ca7c-0147-452d-bd4a-6a1e97e9793e
ms.openlocfilehash: 09fc44dea8d51dbb267d402745c8c2a095b969d8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97243053"
---
# <a name="translation-diagnostics"></a>Traduction : Diagnostics

**ANSI 2.1.1.3** Comment un diagnostic est identifié

Microsoft C génère des messages d'erreur au format suivant :

> *nom du fichier* **(** *numéro de ligne* **) :** *message* de <em>numéro</em> **C** du *diagnostic*

où *filename* est le nom du fichier source dans lequel l’erreur est survenue ; *line-number* correspond au numéro de ligne auquel le compilateur a détecté l’erreur ; *diagnostic* est une erreur ou un avertissement. *number* est un nombre unique à quatre chiffres (précédé d’un **C**, comme indiqué dans la syntaxe) qui identifie l’erreur ou l’avertissement ; *message* est un message explicatif.

## <a name="see-also"></a>Voir aussi

[Comportement défini par l’implémentation](../c-language/implementation-defined-behavior.md)
