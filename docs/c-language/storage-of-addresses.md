---
description: 'En savoir plus sur : stockage des adresses'
title: Stockage des adresses
ms.date: 11/04/2016
helpviewer_keywords:
- storage [C++], addresses
- addresses [C++], storage of
ms.assetid: 423b2402-b847-4788-ad70-943b7c9c5c8b
ms.openlocfilehash: 8f0b51370659d7a23739d75f53492d171c17e422
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97296691"
---
# <a name="storage-of-addresses"></a>Stockage des adresses

La quantité de stockage requis pour une adresse et la signification de l'adresse dépendent de l'implémentation du compilateur. Les pointeurs vers des types différents ne sont pas garantis avoir la même longueur. Par conséquent, **sizeof(char \*)** n'est pas nécessairement égal à **sizeof(int \*)**.

**Spécifique à Microsoft**

Pour le compilateur C Microsoft, **sizeof(char \*)** est égal à **sizeof(int \*)**.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Déclarations de pointeur](../c-language/pointer-declarations.md)
