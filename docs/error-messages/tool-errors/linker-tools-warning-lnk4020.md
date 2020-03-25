---
title: Avertissement des outils Éditeur de liens LNK4020
ms.date: 05/29/2018
f1_keywords:
- LNK4020
helpviewer_keywords:
- LNK4020
ms.openlocfilehash: e818909cc0b590b0f7727846cfd7b469e8bc0e3f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194224"
---
# <a name="linker-tools-warning-lnk4020"></a>Avertissement des outils Éditeur de liens LNK4020

> un enregistrement de type dans'*nom_fichier*'est endommagé ; certains symboles et types ne sont peut-être pas accessibles à partir du débogueur

Le *nom* du fichier PDB comporte un enregistrement de type endommagé.

Ce problème est souvent lié à d’autres problèmes de génération. sauf s’il s’agit du premier problème de génération signalé, traitez d’abord les autres erreurs et avertissements. S’il s’agit du premier problème signalé, vous devrez peut-être nettoyer vos répertoires de build et régénérer votre projet. Si vous utilisez des processus de génération parallèles, vérifiez si l’erreur persiste quand vous sérialisez votre Build.
