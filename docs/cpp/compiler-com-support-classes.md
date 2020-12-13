---
description: 'En savoir plus sur : classes de prise en charge COM du compilateur'
title: Classes du support COM du compilateur
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 6d800d9b-b902-4033-9639-740a30b06f88
ms.openlocfilehash: e2f921e9c3ebe759109d741630afe56f6af30bbc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344703"
---
# <a name="compiler-com-support-classes"></a>Classes du support COM du compilateur

**Spécifique à Microsoft**

Les classes standard sont utilisées pour prendre en charge certains types COM. Les classes sont définies dans \<comdef.h> et les fichiers d’en-tête générés à partir de la bibliothèque de types.

|Classe|Objectif|
|-----------|-------------|
|[_bstr_t](../cpp/bstr-t-class.md)|Encapsule le type `BSTR` pour fournir des opérateurs et des méthodes utiles.|
|[_com_error](../cpp/com-error-class.md)|Définit l’objet d’erreur levé par [_com_raise_error](../cpp/com-raise-error.md) dans la plupart des échecs.|
|[_com_ptr_t](../cpp/com-ptr-t-class.md)|Encapsule les pointeurs d’interface COM et automatise les appels requis à `AddRef` , `Release` et `QueryInterface` .|
|[_variant_t](../cpp/variant-t-class.md)|Encapsule le type `VARIANT` pour fournir des opérateurs et des méthodes utiles.|

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Prise en charge COM du compilateur](../cpp/compiler-com-support.md)<br/>
[Fonctions globales COM du compilateur](../cpp/compiler-com-global-functions.md)<br/>
[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)
