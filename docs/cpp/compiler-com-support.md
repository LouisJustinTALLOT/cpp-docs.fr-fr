---
title: Prise en charge COM du compilateur
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 76a78442-f2a4-4985-9967-67e20773f847
ms.openlocfilehash: e13874bad44610821bed9c588af6bd9124162116
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222211"
---
# <a name="compiler-com-support"></a>Prise en charge COM du compilateur

## <a name="microsoft-specific"></a>Section spécifique à Microsoft

Microsoft C++ compilateur peut directement lire les bibliothèques de types de composant objet model (COM) et traduire le contenu dans C++ code source qui peut être inclus dans la compilation. Les extensions de langage sont disponibles pour simplifier la programmation COM côté client.

À l’aide de la [directive de préprocesseur #import](../preprocessor/hash-import-directive-cpp.md), le compilateur peut lire une bibliothèque de types et les convertir dans un fichier d’en-tête C++ qui décrit le modèle COM des interfaces en tant que classes. Un ensemble d'attributs `#import` est disponible pour permettre le contrôle utilisateur du contenu pour les fichiers d'en-tête de la bibliothèque de types obtenus.

Vous pouvez utiliser la [__declspec](../cpp/declspec.md) attributs étendus [uuid](../cpp/uuid-cpp.md) pour attribuer un identificateur global unique (GUID) à un objet COM. Le mot clé [__uuidof](../cpp/uuidof-operator.md) peut être utilisé pour extraire le GUID associé à un objet COM. Un autre **__declspec** attribut, [propriété](../cpp/property-cpp.md), peut être utilisé pour spécifier le `get` et `set` méthodes pour un membre de données d’un objet COM.

Un ensemble de classes et fonctions globales de prise en charge COM est fourni pour prendre en charge la `VARIANT` et `BSTR` types, implémenter les pointeurs intelligents et encapsuler l’objet d’erreur levé par `_com_raise_error`:

- [Fonctions globales COM du compilateur](../cpp/compiler-com-global-functions.md)

- [_bstr_t](../cpp/bstr-t-class.md)

- [_com_error](../cpp/com-error-class.md)

- [_com_ptr_t](../cpp/com-ptr-t-class.md)

- [_variant_t](../cpp/variant-t-class.md)

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classes du support COM du compilateur](../cpp/compiler-com-support-classes.md)<br/>
[Fonctions globales COM du compilateur](../cpp/compiler-com-global-functions.md)