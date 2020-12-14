---
description: 'En savoir plus sur : erreur irrécupérable C1854'
title: Erreur irrécupérable C1854
ms.date: 11/04/2016
f1_keywords:
- C1854
helpviewer_keywords:
- C1854
ms.assetid: 8c21a9cc-1737-475c-9e57-8725cd8937c1
ms.openlocfilehash: 1c08db55089853545afa511213fc164c978bd4ff
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97276203"
---
# <a name="fatal-error-c1854"></a>Erreur irrécupérable C1854

> Impossible de remplacer les informations obtenues lors de la création de l’en-tête précompilé du fichier objet : '*nom_fichier*'

Vous avez spécifié l’option [/Yu (utiliser un fichier d’en-tête précompilé)](../../build/reference/yu-use-precompiled-header-file.md) après avoir spécifié l’option [/Yc (créer un fichier d’en-tête précompilé)](../../build/reference/yc-create-precompiled-header-file.md) pour le même fichier.

Pour résoudre ce problème, en général, ne définissez qu’un seul fichier dans votre projet à compiler à l’aide de l’option **/Yc** , puis définissez tous les autres fichiers à compiler à l’aide de l’option **/Yu** . Pour plus d’informations sur l’utilisation de l’option **/Yc** et sur la façon de la définir dans l’IDE de Visual Studio, consultez [/Yc (créer un fichier d’en-tête précompilé)](../../build/reference/yc-create-precompiled-header-file.md). Pour plus d’informations sur l’utilisation des en-têtes précompilés, consultez [création de fichiers d’en-tête précompilés](../../build/creating-precompiled-header-files.md).
