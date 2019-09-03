---
title: raw_dispinterfaces importer l’attribut
ms.date: 08/29/2019
f1_keywords:
- raw_dispinterfaces
helpviewer_keywords:
- raw_dispinterfaces attribute
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
ms.openlocfilehash: 73c58b72b27de8dcf96e8ab9464d0fb6bce12b66
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216223"
---
# <a name="raw_dispinterfaces-import-attribute"></a>raw_dispinterfaces importer l’attribut

**C++Plus**

Indique au compilateur de générer des fonctions wrapper de bas niveau pour les méthodes dispinterface, et pour les `IDispatch::Invoke` propriétés qui appellent et retournent le code d’erreur HRESULT.

## <a name="syntax"></a>Syntaxe

> **#import** *bibliothèque de types* **raw_dispinterfaces**

## <a name="remarks"></a>Notes

Si cet attribut n’est pas spécifié, seuls les wrappers de haut niveau sont générés, ce qui lève C++ des exceptions en cas d’échec.

**Spécifique C++ à la fin**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
