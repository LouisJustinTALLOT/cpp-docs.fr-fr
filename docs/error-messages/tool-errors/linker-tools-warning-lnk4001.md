---
title: Avertissement des outils Éditeur de liens LNK4001
ms.date: 11/04/2016
f1_keywords:
- LNK4001
helpviewer_keywords:
- LNK4001
ms.assetid: 0a8b1c3a-64ce-4311-b7c0-065995059246
ms.openlocfilehash: d9659b0cf372ff8ebc225b890fb68866872bb3d6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194406"
---
# <a name="linker-tools-warning-lnk4001"></a>Avertissement des outils Éditeur de liens LNK4001

aucun fichier objet spécifié ; bibliothèques utilisées

L’éditeur de liens a passé un ou plusieurs fichiers. lib, mais aucun fichier. obj.

Étant donné que l’éditeur de liens n’est pas en mesure d’accéder aux informations d’un fichier. lib auquel il peut accéder dans un fichier. obj, cet avertissement indique que vous devez spécifier explicitement d’autres options de l’éditeur de liens. Par exemple, vous devrez peut-être spécifier les options [/machine](../../build/reference/machine-specify-target-platform.md), [/out](../../build/reference/out-output-file-name.md)ou [/entry](../../build/reference/entry-entry-point-symbol.md) .
