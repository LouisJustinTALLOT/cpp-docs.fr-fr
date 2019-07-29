---
title: Prise en charge COM du compilateur
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 76a78442-f2a4-4985-9967-67e20773f847
ms.openlocfilehash: 421930088dcbf9762d50b5af37d994b9008890eb
ms.sourcegitcommit: 720b74dddb1cdf4e570d55103158304ee1df81f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2019
ms.locfileid: "68606377"
---
# <a name="compiler-com-support"></a>Prise en charge COM du compilateur

## <a name="microsoft-specific"></a>Section spécifique à Microsoft

Le compilateur C++ Microsoft peut lire directement les bibliothèques de types COM (Component Object Model) et traduire le C++ contenu dans le code source qui peut être inclus dans la compilation. Les extensions de langage sont disponibles pour faciliter la programmation COM côté client pour les applications de bureau.

En utilisant la [directive de préprocesseur #import](../preprocessor/hash-import-directive-cpp.md), le compilateur peut lire une bibliothèque de types et la convertir en C++ un fichier d’en-tête qui décrit les interfaces COM en tant que classes. Un ensemble d'attributs `#import` est disponible pour permettre le contrôle utilisateur du contenu pour les fichiers d'en-tête de la bibliothèque de types obtenus.

Vous pouvez utiliser l' [UUID](../cpp/uuid-cpp.md) d’attribut étendu [_ _ declspec](../cpp/declspec.md) pour assigner un identificateur global unique (Guid) à un objet com. Le mot clé _ _ [uuidof](../cpp/uuidof-operator.md) peut être utilisé pour extraire le GUID associé à un objet com. Un autre attribut **_ _ declspec** , [Property](../cpp/property-cpp.md), peut être utilisé `get` pour `set` spécifier les méthodes et pour un membre de données d’un objet com.

Un ensemble de classes et de fonctions globales de prise en charge com `VARIANT` est `BSTR` fourni pour prendre en charge les types et, implémenter des pointeurs intelligents `_com_raise_error`et encapsuler l’objet d’erreur levé par:

- [Fonctions globales COM du compilateur](../cpp/compiler-com-global-functions.md)

- [_bstr_t](../cpp/bstr-t-class.md)

- [_com_error](../cpp/com-error-class.md)

- [_com_ptr_t](../cpp/com-ptr-t-class.md)

- [_variant_t](../cpp/variant-t-class.md)

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classes du support COM du compilateur](../cpp/compiler-com-support-classes.md)<br/>
[Fonctions globales COM du compilateur](../cpp/compiler-com-global-functions.md)
