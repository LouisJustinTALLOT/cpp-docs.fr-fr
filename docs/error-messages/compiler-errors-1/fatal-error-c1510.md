---
title: Erreur irrécupérable C1510 | Microsoft Docs
ms.custom: ''
ms.date: 04/11/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1510
dev_langs:
- C++
helpviewer_keywords:
- C1510
ms.assetid: 150c827f-9514-41a9-8d7e-82f820749bcb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d1da6a21e5156ef0b78c42215de5c4ae7e807db
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049694"
---
# <a name="fatal-error-c1510"></a>Erreur irrécupérable C1510

Impossible d'ouvrir la ressource de langage clui.dll

Le compilateur ne peut pas charger la DLL de ressource de langue.

Il existe deux causes courantes de ce problème. Lorsque vous utilisez le compilateur 32 bits et les outils, vous pouvez voir cette erreur pour les grands projets qui utilisent plus de 2 Go de mémoire au cours d’un lien. Une solution possible sur les systèmes Windows 64 bits consiste à utiliser natif 64 bits ou cross compilateur et les outils de génération de votre code. Il tire parti de l’espace mémoire disponible pour les applications 64 bits. Si vous devez utiliser un compilateur 32 bits, car il est en cours d’exécution sur un système 32 bits, dans certains cas, vous pouvez augmenter la quantité de mémoire disponible pour l’éditeur de liens / 3GB. Pour plus d’informations, consultez [4-Gigabyte Tuning : BCDEdit et Boot.ini](https://msdn.microsoft.com/library/vs/alm/bb613473\(v=vs.85\).aspx) et [BCDEdit /Set increaseuserva](https://msdn.microsoft.com/library/ff542202.aspx) commande.

La cause est une installation de Visual Studio rompue ou incomplète. Dans ce cas, exécutez le programme d’installation pour réparer ou réinstaller Visual Studio.
