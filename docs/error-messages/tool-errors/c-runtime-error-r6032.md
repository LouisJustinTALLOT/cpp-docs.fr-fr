---
description: 'En savoir plus sur : erreur Runtime C R6032'
title: Erreur Runtime C R6032
ms.date: 11/04/2016
f1_keywords:
- R6032
helpviewer_keywords:
- R6032
ms.assetid: 52092a63-cc51-444a-bfc3-fad965a3558e
ms.openlocfilehash: b0fbc7730867fb6e9045adf4e5e2b8667f741784
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275891"
---
# <a name="c-runtime-error-r6032"></a>Erreur Runtime C R6032

Espace insuffisant pour les informations relatives aux paramètres régionaux

> [!NOTE]
> Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car elle présente un problème de mémoire interne. Cette erreur peut avoir plusieurs causes, mais elle est souvent due à une condition de mémoire extrêmement faible ou à un bogue dans le programme.
>
> Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :
>
> - Fermez les autres applications en cours d’exécution ou redémarrez votre ordinateur pour libérer de la mémoire.
> - Utilisez la page **applications et fonctionnalités** ou **programmes et fonctionnalités** du **panneau de configuration** pour réparer ou réinstaller le programme.
> - Cochez **Windows Update** dans le **panneau de configuration** pour les mises à jour logicielles.
> - Recherchez une version mise à jour de l’application. Si le problème persiste, contactez le fournisseur de l’application.

**Informations pour les programmeurs**

Le Runtime gère les informations relatives aux paramètres régionaux sur chaque thread afin qu’il puisse traiter les appels aux fonctions sensibles aux paramètres régionaux. Si l’allocation de mémoire pour ces informations échoue, le runtime ne peut pas continuer, car un trop grand nombre de ses fonctionnalités de base en dépendent.
