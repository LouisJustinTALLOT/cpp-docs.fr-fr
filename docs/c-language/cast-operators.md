---
title: Opérateurs de cast | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- cast operators
- type casts, operators
- operators [C++], cast
- type conversion, cast operators
ms.assetid: 43b90bbd-39ef-43e6-ae5d-e8a67a01de40
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: abb4b84519b943d02eca277c9372a128f7d6c2fe
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098501"
---
# <a name="cast-operators"></a>Opérateurs de cast

Un cast de type fournit une méthode pour la conversion explicite du type d'un objet dans une situation spécifique.

## <a name="syntax"></a>Syntaxe

*cast-expression*: *unary-expression*

**(**  *type-name*  **)**  *cast-expression*

Le compilateur traite *cast-expression* comme le type *type-name* après la réalisation d'un cast de type. Les casts peuvent être utilisés pour convertir des objets de tout type scalaire vers ou depuis tout autre type scalaire. Les casts de types explicites sont contraints par les mêmes règles qui déterminent les effets des conversions implicites, présentées dans [Conversions d'assignation](../c-language/assignment-conversions.md). Les restrictions supplémentaires sur les casts peuvent résulter des tailles réelles ou de la représentation des types spécifiques. Consultez [Stockage des types de base](../c-language/storage-of-basic-types.md) pour obtenir plus d'informations sur les tailles réelles des types intégraux. Pour plus d'informations sur les casts de type, consultez [Conversions de cast de type](../c-language/type-cast-conversions.md).

## <a name="see-also"></a>Voir aussi

[Opérateur de cast : ()](../cpp/cast-operator-parens.md)