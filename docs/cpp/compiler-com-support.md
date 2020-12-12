---
description: 'En savoir plus sur : prise en charge du compilateur COM'
title: Prise en charge COM du compilateur
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 76a78442-f2a4-4985-9967-67e20773f847
ms.openlocfilehash: 1dd64d34b39a2b5cd2f0648d38deddf51e8541a3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97120462"
---
# <a name="compiler-com-support"></a>Prise en charge COM du compilateur

**Spécifique à Microsoft**

Le compilateur Microsoft C++ peut lire directement les bibliothèques de types COM (Component Object Model) et traduire le contenu en code source C++ qui peut être inclus dans la compilation. Les extensions de langage sont disponibles pour faciliter la programmation COM côté client pour les applications de bureau.

En utilisant la [directive de préprocesseur #import](../preprocessor/hash-import-directive-cpp.md), le compilateur peut lire une bibliothèque de types et la convertir en un fichier d’en-tête C++ qui décrit les interfaces COM en tant que classes. Un ensemble d'attributs `#import` est disponible pour permettre le contrôle utilisateur du contenu pour les fichiers d'en-tête de la bibliothèque de types obtenus.

Vous pouvez utiliser l' [UUID](../cpp/uuid-cpp.md) d’attribut étendu [__declspec](../cpp/declspec.md) pour assigner un identificateur global unique (Guid) à un objet com. Le mot clé [__uuidof](../cpp/uuidof-operator.md) peut être utilisé pour extraire le GUID associé à un objet com. Un autre **`__declspec`** attribut, [Property](../cpp/property-cpp.md), peut être utilisé pour spécifier les `get` méthodes et `set` pour un membre de données d’un objet com.

Un ensemble de classes et de fonctions globales de prise en charge COM est fourni pour prendre en charge les `VARIANT` `BSTR` types et, implémenter des pointeurs intelligents et encapsuler l’objet d’erreur levé par `_com_raise_error` :

- [Fonctions globales COM du compilateur](../cpp/compiler-com-global-functions.md)

- [_bstr_t](../cpp/bstr-t-class.md)

- [_com_error](../cpp/com-error-class.md)

- [_com_ptr_t](../cpp/com-ptr-t-class.md)

- [_variant_t](../cpp/variant-t-class.md)

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classes de prise en charge COM du compilateur](../cpp/compiler-com-support-classes.md)<br/>
[Fonctions globales COM du compilateur](../cpp/compiler-com-global-functions.md)
