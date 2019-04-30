---
title: Classes du support COM du compilateur
ms.date: 11/04/2016
f1_keywords:
- _com_raise_error
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 6d800d9b-b902-4033-9639-740a30b06f88
ms.openlocfilehash: 066fe797bc500625e96e027777a70f278b88cddb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399198"
---
# <a name="compiler-com-support-classes"></a>Classes du support COM du compilateur

**Section spécifique à Microsoft**

Les classes standard sont utilisées pour prendre en charge certains types COM. Les classes sont définies dans \<comdef.h > et les fichiers d’en-tête générés à partir de la bibliothèque de types.

|Classe|Objectif|
|-----------|-------------|
|[_bstr_t](../cpp/bstr-t-class.md)|Encapsule le type `BSTR` pour fournir des opérateurs et des méthodes utiles.|
|[_com_error](../cpp/com-error-class.md)|Définit l’objet d’erreur levé par [_com_raise_error](../cpp/com-raise-error.md) dans la plupart des échecs.|
|[_com_ptr_t](../cpp/com-ptr-t-class.md)|Encapsule des pointeurs d’interface COM et automatise les appels requis à `AddRef`, `Release`, et `QueryInterface`.|
|[_variant_t](../cpp/variant-t-class.md)|Encapsule le type `VARIANT` pour fournir des opérateurs et des méthodes utiles.|

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Prise en charge COM du compilateur](../cpp/compiler-com-support.md)<br/>
[Fonctions globales COM du compilateur](../cpp/compiler-com-global-functions.md)<br/>
[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)