---
title: Erreur Runtime C R6024 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6024
dev_langs:
- C++
helpviewer_keywords:
- R6024
ms.assetid: 0fb11c0f-9b81-4cab-81bd-4785742946a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 10b258b12bb1ad7e47a7b126b8fd503814186645
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041595"
---
# <a name="c-runtime-error-r6024"></a>Erreur Runtime C R6024

pas assez d’espace pour la table de _onexit/atexit

> [!NOTE]
>  Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car il a un problème de mémoire interne. Cette erreur est généralement dû à une condition de mémoire très faibles, rarement, par un bogue dans le programme ou par une altération des bibliothèques Visual C++ qu’il utilise.
>
>  Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :
>
>  -   Fermez les autres applications en cours d’exécution ou redémarrer votre ordinateur pour libérer la mémoire.
> -   Utilisez le **applications et fonctionnalités** ou **programmes et fonctionnalités** page dans le **le panneau de configuration** pour réparer ou réinstaller le programme.
> -   Utilisez le **applications et fonctionnalités** ou **programmes et fonctionnalités** page dans le **le panneau de configuration** pour réparer ou réinstaller toutes les copies de Microsoft Visual C++ Redistributable.
> -   Vérifiez **mise à jour Windows** dans le **le panneau de configuration** mises à jour logicielles.
> -   Recherchez une version mise à jour de l’application. Contactez le fournisseur de l’application si le problème persiste.

**Informations pour les programmeurs**

Cette erreur se produit, car il n’était pas de mémoire disponible pour le `_onexit` ou `atexit` (fonction). Cette erreur est due à une condition de mémoire insuffisante. Vous pouvez envisager de tampons allocation préalable au démarrage de l’application afin de faciliter l’enregistrement des données de l’utilisateur et pour effectuer une nouvelle application de sortie dans des conditions de mémoire insuffisante.