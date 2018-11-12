---
title: 'Translation : Diagnostics'
ms.date: 11/04/2016
ms.assetid: 3730ca7c-0147-452d-bd4a-6a1e97e9793e
ms.openlocfilehash: 4863b97dc1db7ff295b5f786ca97da2551d0fa62
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50664995"
---
# <a name="translation-diagnostics"></a>Translation : Diagnostics

**ANSI 2.1.1.3** Comment un diagnostic est identifié

Microsoft C génère des messages d'erreur au format suivant :

> *filename* **(** *line-number* **) :** *diagnostic* **C**<em>number</em> *message*

où *filename* est le nom du fichier source dans lequel l’erreur est survenue ; *line-number* correspond au numéro de ligne auquel le compilateur a détecté l’erreur ; *diagnostic* est une erreur ou un avertissement. *number* est un nombre unique à quatre chiffres (précédé d’un **C**, comme indiqué dans la syntaxe) qui identifie l’erreur ou l’avertissement ; *message* est un message explicatif.

## <a name="see-also"></a>Voir aussi

[Comportement défini par l’implémentation](../c-language/implementation-defined-behavior.md)