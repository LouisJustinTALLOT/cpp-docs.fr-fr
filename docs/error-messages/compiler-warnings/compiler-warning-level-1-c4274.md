---
title: Avertissement du compilateur (niveau 1) C4274
ms.date: 11/04/2016
f1_keywords:
- C4274
helpviewer_keywords:
- C4274
ms.assetid: 5a948680-7ed1-469f-978d-ae99d154e161
ms.openlocfilehash: 5f2350f275f883e7bf18aa1621d08b34132e8dfb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175844"
---
# <a name="compiler-warning-level-1-c4274"></a>Avertissement du compilateur (niveau 1) C4274

\#ident ignoré ; consultez la documentation pour #pragma commentaire (exestr, 'String')

La directive `#ident`, qui insère une chaîne spécifiée par l’utilisateur dans l’objet ou le fichier exécutable, est déconseillée. Par conséquent, le compilateur ignore la directive.

> [!CAUTION]
>  Warning C4274 vous conseille d’utiliser la directive [#pragma comment (exestr, 'String')](../../preprocessor/comment-c-cpp.md) . Toutefois, ce Conseil est déconseillé et sera révisé dans une prochaine version du compilateur. Si vous utilisez la directive `#pragma`, l’outil Éditeur de liens (LINK. exe) ignore l’enregistrement de commentaire produit par la directive et émet un avertissement [LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md). Au lieu de la directive `#ident`, nous vous recommandons d’utiliser une chaîne de ressource de version de fichier dans votre application.

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Supprimez la directive `#ident "`*string*`"`.

## <a name="see-also"></a>Voir aussi

[commentaire (C/C++)](../../preprocessor/comment-c-cpp.md)<br/>
[Avertissement des outils Éditeur de liens LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)<br/>
[Utilisation des fichiers de ressources](../../windows/working-with-resource-files.md)
