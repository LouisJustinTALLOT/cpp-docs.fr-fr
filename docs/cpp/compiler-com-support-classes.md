---
title: Classes du support COM du compilateur
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 6d800d9b-b902-4033-9639-740a30b06f88
ms.openlocfilehash: 1a9ff7c57965c9ba00881d5fe48501a6138b31d1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444424"
---
# <a name="compiler-com-support-classes"></a>Classes du support COM du compilateur

**Section spécifique de Microsoft**

Les classes standard sont utilisées pour prendre en charge certains types COM. Les classes sont définies dans \<ComDef. h > et les fichiers d’en-tête générés à partir de la bibliothèque de types.

|Classe|Objectif|
|-----------|-------------|
|[_bstr_t](../cpp/bstr-t-class.md)|Encapsule le type `BSTR` pour fournir des opérateurs et des méthodes utiles.|
|[_com_error](../cpp/com-error-class.md)|Définit l’objet d’erreur levé par [_com_raise_error](../cpp/com-raise-error.md) dans la plupart des échecs.|
|[_com_ptr_t](../cpp/com-ptr-t-class.md)|Encapsule les pointeurs d’interface COM et automatise les appels requis à `AddRef`, `Release`et `QueryInterface`.|
|[_variant_t](../cpp/variant-t-class.md)|Encapsule le type `VARIANT` pour fournir des opérateurs et des méthodes utiles.|

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[Prise en charge COM du compilateur](../cpp/compiler-com-support.md)<br/>
[Fonctions globales COM du compilateur](../cpp/compiler-com-global-functions.md)<br/>
[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)