---
description: 'En savoir plus sur : erreur Runtime C R6002'
title: Erreur Runtime C R6002
ms.date: 11/04/2016
f1_keywords:
- R6002
helpviewer_keywords:
- R6002
ms.assetid: 8fbbe65a-9c43-459e-8342-e1f6d1cef7d0
ms.openlocfilehash: 9f72b249b491ada4f143848a95ed6161695aa023
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97237773"
---
# <a name="c-runtime-error-r6002"></a>Erreur Runtime C R6002

prise en charge de la virgule flottante non chargée

La bibliothèque à virgule flottante nécessaire n’a pas été liée.

> [!NOTE]
> Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car elle présente un problème interne. Il existe plusieurs raisons possibles pour cette erreur, mais elle est souvent due à un défaut dans le code de l’application ou à une tentative d’exécution d’une application qui n’a pas été créée pour votre processeur d’ordinateur particulier.
>
> Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :
>
> - Utilisez la page **applications et fonctionnalités** ou **programmes et fonctionnalités** du **panneau de configuration** pour réparer ou réinstaller le programme.
> - Cochez **Windows Update** dans le **panneau de configuration** pour les mises à jour logicielles.
> - Recherchez une version mise à jour de l’application. Si le problème persiste, contactez le fournisseur de l’application.

**Informations pour les programmeurs**

Cette erreur peut se produire dans votre application lorsque la bibliothèque à virgule flottante n’a pas été liée. Recherchez l’une des causes suivantes :

- Une chaîne de format pour `printf_s` une `scanf_s` fonction ou contenait une spécification de format à virgule flottante et le programme ne contenait pas de variables ou de valeurs à virgule flottante. Pour résoudre ce problème, utilisez un argument à virgule flottante pour correspondre à la spécification de format à virgule flottante, ou effectuez une assignation à virgule flottante ailleurs dans le programme. Cela entraîne le chargement de la prise en charge de la virgule flottante.

- Le compilateur réduit la taille d’un programme en chargeant la prise en charge de virgule flottante uniquement lorsque cela est nécessaire. Le compilateur ne peut pas détecter les opérations à virgule flottante ou les spécifications de format à virgule flottante dans les chaînes de format, donc il ne charge pas les routines à virgule flottante nécessaires. Pour résoudre ce problème, utilisez une spécification de format à virgule flottante et fournissez un argument à virgule flottante, ou effectuez une assignation à virgule flottante ailleurs dans le programme. Cela entraîne le chargement de la prise en charge de la virgule flottante.

- Dans un programme en plusieurs langages, une bibliothèque C a été spécifiée avant une bibliothèque FORTRAN quand le programme a été lié. Reliez et spécifiez la bibliothèque C en dernier.
