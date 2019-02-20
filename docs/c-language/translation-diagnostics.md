---
title: 'Traduction : Diagnostics'
ms.date: 11/04/2016
ms.assetid: 3730ca7c-0147-452d-bd4a-6a1e97e9793e
ms.openlocfilehash: a274b7c5f29b091b2bf29922abfa4d66d3447b47
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152597"
---
# <a name="translation-diagnostics"></a>Traduction : Diagnostics

**ANSI 2.1.1.3** Comment un diagnostic est identifié

Microsoft C génère des messages d'erreur au format suivant :

> *filename* **(** *line-number* **) :** *diagnostic* **C**<em>number</em> *message*

où *filename* est le nom du fichier source dans lequel l’erreur est survenue ; *line-number* correspond au numéro de ligne auquel le compilateur a détecté l’erreur ; *diagnostic* est une erreur ou un avertissement. *number* est un nombre unique à quatre chiffres (précédé d’un **C**, comme indiqué dans la syntaxe) qui identifie l’erreur ou l’avertissement ; *message* est un message explicatif.

## <a name="see-also"></a>Voir aussi

[Comportement défini par l’implémentation](../c-language/implementation-defined-behavior.md)
