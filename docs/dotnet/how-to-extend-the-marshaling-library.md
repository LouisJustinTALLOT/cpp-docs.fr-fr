---
title: 'Comment : étendre la bibliothèque de marshaling'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- Marshaling Library, extending
ms.assetid: 4c4a56d7-1d44-4118-b85f-f9686515e6e9
ms.openlocfilehash: 071ea72a2aa03dcf16eb0f09e121eba4514e5828
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414605"
---
# <a name="how-to-extend-the-marshaling-library"></a>Comment : étendre la bibliothèque de marshaling

Cette rubrique explique comment étendre la bibliothèque de marshaling pour fournir plus de conversions entre les types de données. Les utilisateurs peuvent étendre la bibliothèque de marshaling pour toutes les conversions de données qui ne sont pas actuellement prises en charge par la bibliothèque.

Vous pouvez étendre la bibliothèque de marshaling de l’une des deux manières suivantes : avec ou sans [classe marshal_context](../dotnet/marshal-context-class.md). Consultez la rubrique [vue d’ensemble du marshaling dans C++](../dotnet/overview-of-marshaling-in-cpp.md) pour déterminer si une nouvelle conversion requiert un contexte.

Dans les deux cas, vous créez d’abord un fichier pour les nouvelles conversions de marshaling. Pour préserver l’intégrité des fichiers de la bibliothèque de marshaling standard. Si vous souhaitez déplacer un projet vers un autre ordinateur ou un autre programmeur, vous devez copier le nouveau fichier de marshaling avec le reste du projet. De cette manière, l’utilisateur recevant le projet sera assuré de recevoir les nouvelles conversions et n’aura pas à modifier les fichiers de bibliothèque.

### <a name="to-extend-the-marshaling-library-with-a-conversion-that-does-not-require-a-context"></a>Pour étendre la bibliothèque de marshaling avec une conversion qui ne requiert pas de contexte

1. Créez un fichier pour stocker les nouvelles fonctions de marshaling, par exemple, MyMarshal. h.

1. Incluez un ou plusieurs des fichiers de bibliothèque de Marshal :

   - Marshal. h pour les types de base.

   - marshal_windows. h pour les types de données Windows.

   - marshal_cppstd. h pour les types de données de la bibliothèque standard C++.

   - marshal_atl. h pour les types de données ATL.

1. Utilisez le code à la fin de ces étapes pour écrire la fonction de conversion. Dans ce code, TO est le type vers lequel effectuer la conversion, est le type à partir duquel effectuer la conversion, et `from` est le paramètre à convertir.

1. Remplacez le commentaire relatif à la logique de conversion par du code pour convertir le `from` paramètre en un objet de en type et retourner l’objet converti.

```
namespace msclr {
   namespace interop {
      template<>
      inline TO marshal_as<TO, FROM> (const FROM& from) {
         // Insert conversion logic here, and return a TO parameter.
      }
   }
}
```

### <a name="to-extend-the-marshaling-library-with-a-conversion-that-requires-a-context"></a>Pour étendre la bibliothèque de marshaling avec une conversion qui requiert un contexte

1. Créez un fichier pour stocker les nouvelles fonctions de marshaling, par exemple, MyMarshal. h

1. Incluez un ou plusieurs des fichiers de bibliothèque de Marshal :

   - Marshal. h pour les types de base.

   - marshal_windows. h pour les types de données Windows.

   - marshal_cppstd. h pour les types de données de la bibliothèque standard C++.

   - marshal_atl. h pour les types de données ATL.

1. Utilisez le code à la fin de ces étapes pour écrire la fonction de conversion. Dans ce code, TO est le type vers lequel effectuer la conversion, est le type à partir duquel effectuer la conversion, `toObject` est un pointeur dans lequel stocker le résultat, et `fromObject` est le paramètre à convertir.

1. Remplacez le commentaire à propos de l’initialisation de par le code pour initialiser `toPtr` à la valeur vide appropriée. Par exemple, s’il s’agit d’un pointeur, affectez-lui la valeur `NULL` .

1. Remplacez le commentaire relatif à la logique de conversion par du code pour convertir le `from` paramètre en un objet de *en* type. Cet objet converti sera stocké dans `toPtr` .

1. Remplacez le commentaire relatif au paramètre `toObject` par le code pour définir `toObject` à votre objet converti.

1. Remplacez le commentaire sur le nettoyage des ressources natives par du code pour libérer de la mémoire allouée par `toPtr` . En cas de `toPtr` mémoire allouée à l’aide **`new`** de, utilisez **`delete`** pour libérer la mémoire.

```
namespace msclr {
   namespace interop {
      template<>
      ref class context_node<TO, FROM> : public context_node_base
      {
      private:
         TO toPtr;
      public:
         context_node(TO& toObject, FROM fromObject)
         {
            // (Step 4) Initialize toPtr to the appropriate empty value.
            // (Step 5) Insert conversion logic here.
            // (Step 6) Set toObject to the converted parameter.
         }
         ~context_node()
         {
            this->!context_node();
         }
      protected:
         !context_node()
         {
            // (Step 7) Clean up native resources.
         }
      };
   }
}
```

## <a name="example-extend-marshaling-library"></a>Exemple : étendre une bibliothèque de marshaling

L’exemple suivant étend la bibliothèque de marshaling avec une conversion qui ne requiert pas de contexte. Dans cet exemple, le code convertit les informations sur les employés d’un type de données natif en un type de données managé.

```cpp
// MyMarshalNoContext.cpp
// compile with: /clr
#include <msclr/marshal.h>

value struct ManagedEmp {
   System::String^ name;
   System::String^ address;
   int zipCode;
};

struct NativeEmp {
   char* name;
   char* address;
   int zipCode;
};

namespace msclr {
   namespace interop {
      template<>
      inline ManagedEmp^ marshal_as<ManagedEmp^, NativeEmp> (const NativeEmp& from) {
         ManagedEmp^ toValue = gcnew ManagedEmp;
         toValue->name = marshal_as<System::String^>(from.name);
         toValue->address = marshal_as<System::String^>(from.address);
         toValue->zipCode = from.zipCode;
         return toValue;
      }
   }
}

using namespace System;
using namespace msclr::interop;

int main() {
   NativeEmp employee;

   employee.name = "Jeff Smith";
   employee.address = "123 Main Street";
   employee.zipCode = 98111;

   ManagedEmp^ result = marshal_as<ManagedEmp^>(employee);

   Console::WriteLine("Managed name: {0}", result->name);
   Console::WriteLine("Managed address: {0}", result->address);
   Console::WriteLine("Managed zip code: {0}", result->zipCode);

   return 0;
}
```

Dans l’exemple précédent, la `marshal_as` fonction retourne un handle vers les données converties. Cela a été fait pour empêcher la création d’une copie supplémentaire des données. Le retour direct de la variable aurait un coût de performance inutile qui lui est associé.

```Output
Managed name: Jeff Smith
Managed address: 123 Main Street
Managed zip code: 98111
```

## <a name="example-convert-employee-information"></a>Exemple : convertir des informations sur les employés

L’exemple suivant convertit les informations sur les employés d’un type de données managé en un type de données natif. Cette conversion requiert un contexte de marshaling.

```cpp
// MyMarshalContext.cpp
// compile with: /clr
#include <stdlib.h>
#include <string.h>
#include <msclr/marshal.h>

value struct ManagedEmp {
   System::String^ name;
   System::String^ address;
   int zipCode;
};

struct NativeEmp {
   const char* name;
   const char* address;
   int zipCode;
};

namespace msclr {
   namespace interop {
      template<>
      ref class context_node<NativeEmp*, ManagedEmp^> : public context_node_base
      {
      private:
         NativeEmp* toPtr;
         marshal_context context;
      public:
         context_node(NativeEmp*& toObject, ManagedEmp^ fromObject)
         {
            // Conversion logic starts here
            toPtr = NULL;

            const char* nativeName;
            const char* nativeAddress;

            // Convert the name from String^ to const char*.
            System::String^ tempValue = fromObject->name;
            nativeName = context.marshal_as<const char*>(tempValue);

            // Convert the address from String^ to const char*.
            tempValue = fromObject->address;
            nativeAddress = context.marshal_as<const char*>(tempValue);

            toPtr = new NativeEmp();
            toPtr->name = nativeName;
            toPtr->address = nativeAddress;
            toPtr->zipCode = fromObject->zipCode;

            toObject = toPtr;
         }
         ~context_node()
         {
            this->!context_node();
         }
      protected:
         !context_node()
         {
            // When the context is deleted, it will free the memory
            // allocated for toPtr->name and toPtr->address, so toPtr
            // is the only memory that needs to be freed.
            if (toPtr != NULL) {
               delete toPtr;
               toPtr = NULL;
            }
         }
      };
   }
}

using namespace System;
using namespace msclr::interop;

int main() {
   ManagedEmp^ employee = gcnew ManagedEmp();

   employee->name = gcnew String("Jeff Smith");
   employee->address = gcnew String("123 Main Street");
   employee->zipCode = 98111;

   marshal_context context;
   NativeEmp* result = context.marshal_as<NativeEmp*>(employee);

   if (result != NULL) {
      printf_s("Native name: %s\nNative address: %s\nNative zip code: %d\n",
         result->name, result->address, result->zipCode);
   }

   return 0;
}
```

```Output
Native name: Jeff Smith
Native address: 123 Main Street
Native zip code: 98111
```

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble du marshaling en C++](../dotnet/overview-of-marshaling-in-cpp.md)
