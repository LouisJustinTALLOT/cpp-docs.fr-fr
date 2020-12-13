---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4274'
title: Avertissement du compilateur (niveau 1) C4274
ms.date: 11/04/2016
f1_keywords:
- C4274
helpviewer_keywords:
- C4274
ms.assetid: 5a948680-7ed1-469f-978d-ae99d154e161
ms.openlocfilehash: aa1f6d3b07c7d788d9e47955c4bb51930522b7a3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340097"
---
# <a name="compiler-warning-level-1-c4274"></a>Avertissement du compilateur (niveau 1) C4274

\#ident ignoré ; consultez la documentation pour #pragma commentaire (exestr, 'String')

La `#ident` directive, qui insère une chaîne spécifiée par l’utilisateur dans l’objet ou le fichier exécutable, est déconseillée. Par conséquent, le compilateur ignore la directive.

> [!CAUTION]
> Warning C4274 vous conseille d’utiliser la directive [#pragma comment (exestr, 'String')](../../preprocessor/comment-c-cpp.md) . Toutefois, ce Conseil est déconseillé et sera révisé dans une prochaine version du compilateur. Si vous utilisez la `#pragma` directive, l’outil Éditeur de liens (LINK.exe) ignore l’enregistrement de commentaire produit par la directive et émet un avertissement [LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md). Au lieu de la `#ident` directive, nous vous recommandons d’utiliser une chaîne de ressource de version de fichier dans votre application.

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Supprimez la directive de `#ident "` *chaîne* `"` .

## <a name="see-also"></a>Voir aussi

[commentaire (C/C++)](../../preprocessor/comment-c-cpp.md)<br/>
[Avertissement des outils Éditeur de liens LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)<br/>
[Utilisation des fichiers de ressources](../../windows/working-with-resource-files.md)
