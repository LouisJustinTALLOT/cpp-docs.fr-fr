---
title: 'Translation : Diagnostics | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 3730ca7c-0147-452d-bd4a-6a1e97e9793e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d297cfd4f4dee49d3344ae2f159f85682f05ea2f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46017584"
---
# <a name="translation-diagnostics"></a>Translation : Diagnostics

**ANSI 2.1.1.3** Comment un diagnostic est identifié

Microsoft C génère des messages d'erreur au format suivant :

> *filename* **(** *line-number* **) :** *diagnostic* **C**<em>number</em> *message*

où *filename* est le nom du fichier source dans lequel l’erreur est survenue ; *line-number* correspond au numéro de ligne auquel le compilateur a détecté l’erreur ; *diagnostic* est une erreur ou un avertissement. *number* est un nombre unique à quatre chiffres (précédé d’un **C**, comme indiqué dans la syntaxe) qui identifie l’erreur ou l’avertissement ; *message* est un message explicatif.

## <a name="see-also"></a>Voir aussi

[Comportement défini par l’implémentation](../c-language/implementation-defined-behavior.md)