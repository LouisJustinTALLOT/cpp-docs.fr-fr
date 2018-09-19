---
title: Erreur des LNK1164 des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1164
dev_langs:
- C++
helpviewer_keywords:
- LNK1164
ms.assetid: da89765c-affa-4f88-b170-6d6b19a577cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b07dcf360a58b07b84abe655641b758d6137d0e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087428"
---
# <a name="linker-tools-error-lnk1164"></a>Erreur des outils Éditeur de liens LNK1164

section alignement des sections (nombre) supérieur à la valeur /ALIGN

La taille d’alignement pour la section donnée dans le fichier objet dépasse la valeur spécifiée avec le [/aligner](../../build/reference/align-section-alignment.md) option. Le **/aligner** valeur doit être une puissance de 2 égale ou supérieure à l’alignement de section donné dans le fichier objet.

Une recompilation avec une plus petite alignement de section ou augmenter la **/aligner** valeur.