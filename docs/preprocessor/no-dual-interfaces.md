---
description: 'En savoir plus sur les éléments suivants : no_dual_interfaces l’attribut import'
title: no_dual_interfaces l’attribut d’importation
ms.date: 08/29/2019
f1_keywords:
- no_dual_interfaces
helpviewer_keywords:
- no_dual_interfaces attribute
ms.assetid: 9acd5d9d-4a49-4cdc-9470-73a2c23cf512
ms.openlocfilehash: 1c3010b252ac71e38312fa193520938fbb4d681a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333343"
---
# <a name="no_dual_interfaces-import-attribute"></a>no_dual_interfaces l’attribut d’importation

**Section spécifique à C++**

Modifie la façon dont le compilateur génère des fonctions wrapper pour les méthodes d'interface double.

## <a name="syntax"></a>Syntaxe

>  *bibliothèque de types* #import **no_dual_interfaces**

## <a name="remarks"></a>Notes

Normalement, le wrapper appelle la méthode par le biais de la table de fonctions virtuelles pour l’interface. Avec **no_dual_interfaces**, le wrapper appelle plutôt `IDispatch::Invoke` pour appeler la méthode.

**FIN de la section spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
