---
title: Erreur du compilateur C2338
ms.date: 11/04/2016
f1_keywords:
- C2338
helpviewer_keywords:
- C2338
ms.assetid: 49bba575-1de4-4963-86c6-ce3226a2ba51
ms.openlocfilehash: 2a76ecaf78b117b0c1acabd9fcd50c9ae0f73b98
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188294"
---
# <a name="compiler-error-c2338"></a>Erreur du compilateur C2338

> *message d’erreur*

Cette erreur peut être provoquée par un `static_assert` erreur pendant la compilation. Le message est fourni par le `static_assert` paramètres.

Ce message d’erreur peut également être généré par des fournisseurs externes au compilateur. Dans la plupart des cas, ces erreurs sont signalées par un fournisseur d’attributs DLL, telle que ATLPROV. Certaines formes courantes de ce message sont les suivantes :

- «*attribut*' Atl Attribute Provider : erreur ATL*nombre* *message*

- Utilisation incorrecte de l’attribut '*attribut*'

- «*utilisation*' : format incorrect pour l’attribut 'utilisation'

Ces erreurs sont souvent irrécupérables et peuvent être suivies d’une erreur irrécupérable du compilateur.

Pour résoudre ces problèmes, corrigez l’utilisation d’attribut. Par exemple, dans certains cas, les paramètres de l’attribut doivent être déclarés avant de pouvoir être utilisés. Si un numéro d’erreur ATL est fourni, consultez la documentation de cette erreur pour plus d’informations.
