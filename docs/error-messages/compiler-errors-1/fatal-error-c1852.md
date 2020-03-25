---
title: Erreur irrécupérable C1852
ms.date: 11/04/2016
f1_keywords:
- C1852
helpviewer_keywords:
- C1852
ms.assetid: fa011004-b8d6-46f1-ba80-4785e4ce137f
ms.openlocfilehash: 540febabc8f2947f11b58cf7eadee53d47f7bef3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202876"
---
# <a name="fatal-error-c1852"></a>Erreur irrécupérable C1852

'nom_fichier' n’est pas un fichier d’en-tête précompilé valide

Le fichier n’est pas un en-tête précompilé.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Fichier non valide spécifié avec **/Yu** ou **#pragma hdrstop**.

1. Le compilateur suppose que l’extension de fichier est .pch, sauf indication contraire de votre part.
