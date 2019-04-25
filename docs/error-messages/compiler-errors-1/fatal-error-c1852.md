---
title: Erreur irrécupérable C1852
ms.date: 11/04/2016
f1_keywords:
- C1852
helpviewer_keywords:
- C1852
ms.assetid: fa011004-b8d6-46f1-ba80-4785e4ce137f
ms.openlocfilehash: 895c2fc988c9566f9e50b1ac1a18eb4dc1c6661a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165734"
---
# <a name="fatal-error-c1852"></a>Erreur irrécupérable C1852

'nom_fichier' n’est pas un fichier d’en-tête précompilé valide

Le fichier n’est pas un en-tête précompilé.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Fichier non valide spécifié avec **/Yu** ou **#pragma hdrstop**.

1. Le compilateur suppose que l’extension de fichier est .pch, sauf indication contraire de votre part.