---
description: 'En savoir plus sur : erreur irrécupérable C1005'
title: Erreur irrécupérable C1005
ms.date: 11/04/2016
f1_keywords:
- C1005
helpviewer_keywords:
- C1005
ms.assetid: 150daf8e-a38a-4669-9c1a-a05b5a1f65ef
ms.openlocfilehash: c57856a09aa3473c7f5ba3049a2962fb4553e4e5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97262670"
---
# <a name="fatal-error-c1005"></a>Erreur irrécupérable C1005

chaîne trop grande pour la mémoire tampon

Une chaîne dans un fichier intermédiaire du compilateur a entraîné un dépassement de mémoire tampon.

Vous pouvez obtenir cette erreur quand le paramètre que vous passez aux options de compilateur [/Fd](../../build/reference/fd-program-database-file-name.md) ou [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) est supérieur à 256 octets.
