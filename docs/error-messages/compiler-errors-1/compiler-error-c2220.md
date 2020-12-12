---
description: 'En savoir plus sur : erreur du compilateur C2220'
title: Erreur du compilateur C2220
ms.date: 11/04/2016
f1_keywords:
- C2220
helpviewer_keywords:
- C2220
ms.assetid: d610802c-64d7-40ad-a2a6-0ed0b6815a6c
ms.openlocfilehash: f45a34d0cdaa5e82c3f5e6c051126c6df4eb2005
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245432"
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
