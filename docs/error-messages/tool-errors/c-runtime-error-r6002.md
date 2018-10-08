---
title: Erreur Runtime C R6002 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6002
dev_langs:
- C++
helpviewer_keywords:
- R6002
ms.assetid: 8fbbe65a-9c43-459e-8342-e1f6d1cef7d0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cde499e919a7b222a41229576ef3b2d37d55d648
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860640"
---
# <a name="c-runtime-error-r6002"></a>Erreur Runtime C R6002

prise en charge à virgule flottante n’a ne pas chargé

La bibliothèque à virgule flottante nécessaire n’était pas liée.

> [!NOTE]
> Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car il a un problème interne. Il existe plusieurs raisons possibles à cette erreur, mais souvent, elle est provoquée par un défaut dans le code de l’application, ou en essayant d’exécuter une application qui n’a pas été générée pour le processeur de votre ordinateur particulier.
>
> Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :
>
> - Utilisez le **applications et fonctionnalités** ou **programmes et fonctionnalités** page dans le **le panneau de configuration** pour réparer ou réinstaller le programme.
> - Vérifiez **mise à jour Windows** dans le **le panneau de configuration** mises à jour logicielles.
> - Recherchez une version mise à jour de l’application. Contactez le fournisseur de l’application si le problème persiste.

**Informations pour les programmeurs**

Cette erreur peut se produire dans votre application lors de la bibliothèque à virgule flottante n’était pas liée. Recherchez une de ces causes :

- Une chaîne de format pour un `printf_s` ou `scanf_s` fonction contenait une spécification de format à virgule flottante et le programme ne contenait pas les valeurs à virgule flottante ou les variables. Pour résoudre ce problème, utilisez un argument à virgule flottante pour qu’elles correspondent à la spécification de format à virgule flottante, ou procédez à une assignation à virgule flottante ailleurs dans le programme. Cela entraîne une prise en charge à virgule flottante à charger.

- Le compilateur réduit la taille d’un programme en chargeant une prise en charge à virgule flottante uniquement lorsque cela est nécessaire. Le compilateur ne peut pas détecter les opérations à virgule flottante ou spécifications de format à virgule flottante dans les chaînes de format, donc il ne charge pas les routines à virgule flottante nécessaires. Pour résoudre ce problème, utilisez une spécification de format à virgule flottante et fournissez un argument à virgule flottante ou effectuer une assignation à virgule flottante ailleurs dans le programme. Cela entraîne une prise en charge à virgule flottante à charger.

- Dans un programme de plusieurs langages, une bibliothèque C a été spécifiée avant une bibliothèque FORTRAN lorsque le programme a été lié. Reliez et spécifiez la bibliothèque C de dernière.