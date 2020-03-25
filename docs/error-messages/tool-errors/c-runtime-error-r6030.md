---
title: Erreur Runtime C R6030
ms.date: 11/04/2016
f1_keywords:
- R6030
helpviewer_keywords:
- R6030
ms.assetid: 0238a6c3-a033-4046-8adc-f8f99d961153
ms.openlocfilehash: 5d7160623d4e1eb83240c09e637c780fefc0d43d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197117"
---
# <a name="c-runtime-error-r6030"></a>Erreur Runtime C R6030

CRT non initialisé

> [!NOTE]
> Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car elle présente un problème interne. Ce problème est le plus souvent causé par certains programmes logiciels de sécurité, ou rarement, par un bogue dans le programme.
>
> Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :
>
> - Votre logiciel de sécurité peut contenir des instructions spécifiques pour atténuer ce problème. Pour plus d’informations, consultez le site Web de votre fournisseur de logiciels de sécurité. Vous pouvez également rechercher les versions mises à jour de votre logiciel de sécurité ou essayer différents logiciels de sécurité.
> - Utilisez la page **applications et fonctionnalités** ou **programmes et fonctionnalités** du **panneau de configuration** pour réparer ou réinstaller le programme.
> - Cochez **Windows Update** dans le **panneau de configuration** pour les mises à jour logicielles.
> - Recherchez une version mise à jour de l’application. Si le problème persiste, contactez le fournisseur de l’application.

**Informations pour les programmeurs**

Cette erreur se produit si vous utilisez le runtime C (CRT), mais que le code de démarrage du CRT n’a pas été exécuté. Il est possible d’obtenir cette erreur si le commutateur de l’éditeur de liens [/entry](../../build/reference/entry-entry-point-symbol.md) est utilisé pour remplacer l’adresse de départ par défaut, généralement **mainCRTStartup**, **wmainCRTStartup** pour un exe de console, **WinMainCRTStartup** ou **wWinMainCRTStartup** pour un exe Windows, ou **_DllMainCRTStartup** pour une dll. À moins que l’une des fonctions ci-dessus ne soit appelée au démarrage, le runtime C ne sera pas initialisé. Ces fonctions de démarrage sont généralement appelées par défaut lorsque vous liez à la bibliothèque Runtime C et utilisent les points d’entrée **principaux**, **wmain**, **WinMain**ou **DllMain** normaux.

Vous pouvez également recevoir cette erreur lorsqu’un autre programme utilise des techniques d’injection de code pour intercepter certains appels de bibliothèque DLL. Certains programmes de sécurité intrusifs utilisent cette technique. Dans les versions de C++ Visual antérieures à visual studio 2015, il est possible d’utiliser une bibliothèque CRT liée de manière statique pour résoudre le problème, mais cela n’est pas recommandé pour des raisons de sécurité et de mise à jour d’application. La correction de ce problème peut nécessiter l’intervention de l’utilisateur final.
