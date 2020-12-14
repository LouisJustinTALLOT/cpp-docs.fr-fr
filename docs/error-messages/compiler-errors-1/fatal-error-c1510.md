---
description: 'En savoir plus sur : erreur irrécupérable C1510'
title: Erreur irrécupérable C1510
ms.date: 04/11/2017
f1_keywords:
- C1510
helpviewer_keywords:
- C1510
ms.assetid: 150c827f-9514-41a9-8d7e-82f820749bcb
ms.openlocfilehash: 3112874f033fdeed4cc4290b2469105a275baed8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97276320"
---
# <a name="fatal-error-c1510"></a>Erreur irrécupérable C1510

Impossible d'ouvrir la ressource de langage clui.dll

Le compilateur ne peut pas charger la DLL de ressources de langage.

Il existe deux causes courantes à ce problème. Lorsque vous utilisez le compilateur et les outils 32 bits, vous pouvez voir cette erreur pour les grands projets qui utilisent plus de 2 Go de mémoire pendant un lien. Une solution possible sur les systèmes Windows 64 bits consiste à utiliser le compilateur et les outils natifs ou croisés 64 bits pour générer votre code. Cela tire parti de l’espace mémoire plus important disponible pour les applications 64 bits. Si vous devez utiliser un compilateur 32 bits, car vous exécutez sur un système 32 bits, vous pouvez, dans certains cas, augmenter la quantité de mémoire disponible pour l’éditeur de liens à 3 Go. Pour plus d’informations, consultez [réglage à 4 gigaoctets : bcdedit et Boot.ini](/windows/win32/memory/4-gigabyte-tuning) et la commande [bcdedit/set increaseuserva](/windows-hardware/drivers/devtest/bcdedit--set) .

L’autre cause courante est une installation de Visual Studio interrompue ou incomplète. Dans ce cas, réexécutez le programme d’installation pour réparer ou réinstaller Visual Studio.
