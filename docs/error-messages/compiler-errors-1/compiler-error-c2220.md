---
title: Erreur du compilateur C2220 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2220
dev_langs:
- C++
helpviewer_keywords:
- C2220
ms.assetid: d610802c-64d7-40ad-a2a6-0ed0b6815a6c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f4179b396e732ceeea20aeb9428d841a357a6d1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051319"
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