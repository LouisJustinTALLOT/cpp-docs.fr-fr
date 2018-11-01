---
title: Erreur du compilateur C2338
ms.date: 11/04/2016
f1_keywords:
- C2338
helpviewer_keywords:
- C2338
ms.assetid: 49bba575-1de4-4963-86c6-ce3226a2ba51
ms.openlocfilehash: 4ca3feb2a71efa60229afdbf918109a5d5d59cad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539592"
---
# <a name="compiler-error-c2338"></a>Erreur du compilateur C2338

> *message d’erreur*

Cette erreur peut être provoquée par un `static_assert` erreur pendant la compilation. Le message est fourni par le `static_assert` paramètres.

Ce message d’erreur peut également être généré par des fournisseurs externes au compilateur. Dans la plupart des cas, ces erreurs sont signalées par un fournisseur d’attributs DLL, telle que ATLPROV. Certaines formes courantes de ce message sont les suivantes :

> «*attribut*' Atl Attribute Provider : erreur ATL*nombre* *message*

> Utilisation incorrecte de l’attribut '*attribut*'

> «*utilisation*' : format incorrect pour l’attribut 'utilisation'

Ces erreurs sont souvent irrécupérables et peuvent être suivies d’une erreur irrécupérable du compilateur.

Pour résoudre ces problèmes, corrigez l’utilisation d’attribut. Par exemple, dans certains cas, les paramètres de l’attribut doivent être déclarés avant de pouvoir être utilisés. Si un numéro d’erreur ATL est fourni, consultez la documentation de cette erreur pour plus d’informations.
