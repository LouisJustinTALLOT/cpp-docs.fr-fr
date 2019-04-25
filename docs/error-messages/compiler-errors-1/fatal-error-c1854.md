---
title: Erreur irrécupérable C1854
ms.date: 11/04/2016
f1_keywords:
- C1854
helpviewer_keywords:
- C1854
ms.assetid: 8c21a9cc-1737-475c-9e57-8725cd8937c1
ms.openlocfilehash: 83eb5e01eac377b8f19a0e94dc1518e3ed557c3b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165636"
---
# <a name="fatal-error-c1854"></a>Erreur irrécupérable C1854

> ne peut pas remplacer les informations obtenues lors de la création de l’en-tête précompilé du fichier objet : '*filename*'

Que vous avez spécifié le [/Yu (utiliser un en-tête précompilé)](../../build/reference/yu-use-precompiled-header-file.md) option après avoir spécifié le [/Yc (créer un fichier d’en-tête précompilé)](../../build/reference/yc-create-precompiled-header-file.md) option pour le même fichier.

Pour résoudre ce problème, en général, ne définir qu’un seul fichier dans votre projet doit être compilé à l’aide de la **/Yc** option et définissez tous les autres fichiers à compiler à l’aide de la **/Yu** option. Pour plus d’informations sur l’utilisation de la **/Yc** option et comment la définir dans l’IDE Visual Studio, consultez [/Yc (créer un fichier d’en-tête précompilé)](../../build/reference/yc-create-precompiled-header-file.md). Pour plus d’informations sur l’utilisation d’en-têtes précompilés, consultez [création de fichiers d’en-tête précompilés](../../build/creating-precompiled-header-files.md).
