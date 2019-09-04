---
title: no_dual_interfaces importer l’attribut
ms.date: 08/29/2019
f1_keywords:
- no_dual_interfaces
helpviewer_keywords:
- no_dual_interfaces attribute
ms.assetid: 9acd5d9d-4a49-4cdc-9470-73a2c23cf512
ms.openlocfilehash: 6270888f0d31e4fbe18fb3364995be8c73426b83
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220765"
---
# <a name="no_dual_interfaces-import-attribute"></a>no_dual_interfaces importer l’attribut

**C++Plus**

Modifie la façon dont le compilateur génère des fonctions wrapper pour les méthodes d'interface double.

## <a name="syntax"></a>Syntaxe

> **#import** *bibliothèque de types* **no_dual_interfaces**

## <a name="remarks"></a>Notes

Normalement, le wrapper appelle la méthode par le biais de la table de fonctions virtuelles pour l’interface. Avec **no_dual_interfaces**, le wrapper appelle `IDispatch::Invoke` plutôt pour appeler la méthode.

**Spécifique C++ à la fin**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
