---
description: 'En savoir plus sur : erreur du compilateur C3505'
title: Erreur du compilateur C3505
ms.date: 11/04/2016
f1_keywords:
- C3505
helpviewer_keywords:
- C3505
ms.assetid: ed73c99e-93a1-4f3a-bac7-ba7ed5d836e4
ms.openlocfilehash: 10727b04ce587eb56872440ad7d46dd544eb0642
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113111"
---
# <a name="compiler-error-c3505"></a>Erreur du compilateur C3505

> Impossible de charger la bibliothèque de types'*GUID*'

C3505 peut être provoquée si vous exécutez le compilateur croisé entre les versions 32 bits, x86-Host pour 64 bits et x64 sur un ordinateur 64 bits, car le compilateur s’exécute sous WOW64 et peut uniquement lire à partir de la ruche de Registre 32 bits.

Vous pouvez résoudre cette erreur en générant à la fois les versions 32 bits et 64 bits de la bibliothèque de types que vous essayez d’importer, puis les inscrire toutes les deux.  Vous pouvez utiliser le compilateur 64 bits natif, qui vous oblige à modifier votre propriété de **Répertoires VC + +** dans l’IDE pour pointer vers le compilateur 64 bits.

Pour plus d'informations, consultez

- [Guide pratique pour activer un ensemble d’outils du compilateur Visual C++ 64 bits sur la ligne de commande](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)

- [Guide pratique pour configurer des projets Visual C++ pour cibler des plateformes x64 64 bits](../../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)
