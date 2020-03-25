---
title: Erreur du compilateur C2220
ms.date: 11/04/2016
f1_keywords:
- C2220
helpviewer_keywords:
- C2220
ms.assetid: d610802c-64d7-40ad-a2a6-0ed0b6815a6c
ms.openlocfilehash: c4fdac833e69e748dd29b9cf772c167fc1dbbd00
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206659"
---
# <a name="compiler-error-c2220"></a>Erreur du compilateur C2220

AVERTISSEMENT traité en tant qu’erreur : aucun fichier objet généré

[/WX](../../build/reference/compiler-option-warning-level.md) indique au compilateur de traiter tous les avertissements comme des erreurs. Comme une erreur s’est produite, aucun objet ou fichier exécutable n’a été généré.

Cette erreur apparaît uniquement lorsque l’indicateur **/WX** est défini et qu’un avertissement se produit pendant la compilation. Pour corriger cette erreur, vous devez éliminer chaque avertissement dans votre projet.

### <a name="to-fix-use-one-of-the-following-techniques"></a>Pour résoudre ce problème, utilisez l’une des techniques suivantes :

- Corrigez les problèmes qui provoquent des avertissements dans votre projet.

- Compilez à un niveau d’avertissement inférieur : par exemple, utilisez **/W3** au lieu de **/W4**.

- Utilisez un pragma [Warning](../../preprocessor/warning.md) pour désactiver ou supprimer un avertissement spécifique.

- N’utilisez pas **/WX** pour compiler.
