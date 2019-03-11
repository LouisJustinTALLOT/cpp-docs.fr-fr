---
title: Platform::Metadata::RuntimeClassName
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Metadata::RuntimeClassName
helpviewer_keywords:
- RuntimeClassName
- Platform::Metadata::RuntimeClassName
ms.assetid: fdef8f85-ab94-4edd-ba50-ee0da9358ff6
ms.openlocfilehash: d3de753c3a8897058333e02ce4294a0780d5b818
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57738555"
---
# <a name="platformmetadataruntimeclassname"></a>Platform::Metadata::RuntimeClassName

Lorsqu'une classe privée est appliquée à une définition de classe, elle assure le retour d'un nom valide à partir de la fonction GetRuntimeClassName.

## <a name="syntax"></a>Syntaxe

```cpp
[Platform::Metadata::RuntimeClassName] name
```

#### <a name="parameters"></a>Paramètres

*name*<br/>
Le nom d'un type public existant visible dans le Windows Runtime.

### <a name="remarks"></a>Notes

Utilisez cet attribut sur des classes ref privées pour spécifier un nom de type de runtime personnalisé et/ou lorsque le nom existant ne répond pas aux spécifications. Spécifiez une interface publique en tant que nom, que la classe implémente.

### <a name="example"></a>Exemple

L'exemple suivant montre comment utiliser l'attribut. Dans cet exemple, le nom de type de runtime HellowWorldImpl est Test::Native::MyComponent::IHelloWorld

```cpp
namespace Test
{
    namespace Native
    {
        namespace MyComponent
        {
            public interface class IHelloWorld
            {
                Platform::String^ SayHello();
            };

            private ref class HelloWorldImpl sealed :[Platform::Metadata::RuntimeClassName] IHelloWorld
            {
            public:
                HelloWorldImpl();
                virtual Platform::String^ SayHello();
            };

            Platform::String^ HelloWorldImpl::SayHello()
            {
                return L"Hello World!";
            }
        }
    }
}
```

## <a name="see-also"></a>Voir aussi

[Platform::Metadata (espace de noms)](../cppcx/platform-metadata-namespace.md)
