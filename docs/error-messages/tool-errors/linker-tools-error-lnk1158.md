---
description: 'En savoir plus sur : erreur des outils Éditeur de liens LNK1158'
title: Erreur des outils Éditeur de liens LNK1158
ms.date: 11/04/2016
f1_keywords:
- LNK1158
helpviewer_keywords:
- LNK1158
ms.assetid: 45febf16-d9e1-42db-af91-532e2717fd6a
ms.openlocfilehash: ea5c362de51cbf1f884f38fa4311eef557565573
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97343962"
---
# <a name="linker-tools-error-lnk1158"></a>Erreur des outils Éditeur de liens LNK1158

Impossible d’exécuter’nom_fichier'

Le fichier exécutable donné appelé par [Link](../../build/reference/linking.md) n’est pas dans le répertoire qui contient le lien ni dans un répertoire spécifié dans la variable d’environnement PATH.

Par exemple, vous obtiendrez cette erreur si vous essayez d’utiliser le paramètre PGOPTIMIZE à l’option de l’éditeur de liens [/LTCG](../../build/reference/ltcg-link-time-code-generation.md) sur un ordinateur doté d’un système d’exploitation 32 bits.
