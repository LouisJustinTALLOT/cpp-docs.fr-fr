---
title: Erreur du compilateur C2220
ms.date: 11/04/2016
f1_keywords:
- C2220
helpviewer_keywords:
- C2220
ms.assetid: d610802c-64d7-40ad-a2a6-0ed0b6815a6c
ms.openlocfilehash: 3ff730c6fea7d2c57c4ec3054fc627cdc6227e2d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62311746"
---
# <a name="compiler-error-c2220"></a>Erreur du compilateur C2220

Avertissement considéré comme une erreur - aucun fichier objet généré

[/WX](../../build/reference/compiler-option-warning-level.md) indique au compilateur de traiter tous les avertissements comme des erreurs. Une erreur est survenue, aucun objet ou le fichier exécutable a été généré.

Cette erreur apparaît uniquement lorsque le **/WX** indicateur est défini et un avertissement se produit pendant la compilation. Pour corriger cette erreur, vous devez éliminer chaque avertissement dans votre projet.

### <a name="to-fix-use-one-of-the-following-techniques"></a>Pour résoudre le problème, utilisez une des techniques suivantes

- Résoudre les problèmes qui provoquent des avertissements dans votre projet.

- Compiler à un niveau d’avertissement inférieur, par exemple, utilisez **w3** au lieu de **/W4**.

- Utilisez un [avertissement](../../preprocessor/warning.md) pragma pour désactiver ou supprimer un avertissement spécifique.

- N’utilisez pas **/WX** à compiler.