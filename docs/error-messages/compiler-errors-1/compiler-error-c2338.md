---
title: Erreur du compilateur C2338
ms.date: 11/04/2016
f1_keywords:
- C2338
helpviewer_keywords:
- C2338
ms.assetid: 49bba575-1de4-4963-86c6-ce3226a2ba51
ms.openlocfilehash: c92a95b97cb4c57d3ad5cfbf8fe1d9980d5362cd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221209"
---
# <a name="compiler-error-c2338"></a>Erreur du compilateur C2338

> *Message d’erreur*

Cette erreur peut être due à une **`static_assert`** erreur lors de la compilation. Le message est fourni par les **`static_assert`** paramètres.

Ce message d’erreur peut également être généré par des fournisseurs externes dans le compilateur. Dans la plupart des cas, ces erreurs sont signalées par une DLL de fournisseur d’attributs, telle que ATLPROV. Voici quelques formes courantes de ce message :

- Fournisseur d’attributs ATL'*attribut*' : *message* d’erreur de*numéro* ATL

- Utilisation incorrecte de l’attribut'*attribut*'

- '*usage*' : format incorrect pour l’attribut’usage'

Ces erreurs sont souvent irrécupérables et peuvent être suivies par une erreur irrécupérable du compilateur.

Pour résoudre ces problèmes, corrigez l’utilisation des attributs. Par exemple, dans certains cas, les paramètres d’attribut doivent être déclarés avant de pouvoir être utilisés. Si un numéro d’erreur ATL est fourni, consultez la documentation relative à cette erreur pour obtenir des informations plus spécifiques.
