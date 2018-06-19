---
title: 'Comment : étendre la bibliothèque de Marshaling | Documents Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Marshaling Library, extending
ms.assetid: 4c4a56d7-1d44-4118-b85f-f9686515e6e9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6f6503cbb0006c0c8b2e1ed113a798a23ac2ff55
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33135883"
---
# <a name="how-to-extend-the-marshaling-library"></a>Comment : étendre la bibliothèque de marshaling
Cette rubrique explique comment étendre la bibliothèque de marshaling pour fournir plus de conversions entre types de données. Les utilisateurs peuvent étendre la bibliothèque de marshaling pour les conversions de données non prises en charge par la bibliothèque.  
  
 Vous pouvez étendre la bibliothèque de marshaling de deux façons différentes - avec ou sans un [marshal_context, classe](../dotnet/marshal-context-class.md). Examinez le [vue d’ensemble du Marshaling dans C++](../dotnet/overview-of-marshaling-in-cpp.md) rubrique pour déterminer si une nouvelle conversion requiert un contexte.  
  
 Dans les deux cas, vous créez tout d’abord un fichier pour les nouvelles conversions de marshaling. Faire afin de préserver l’intégrité des fichiers de la bibliothèque de marshaling standard. Si vous souhaitez porter un projet vers un autre ordinateur ou un autre programmeur, vous devez copier le nouveau fichier marshaling avec le reste du projet. De cette manière, l’utilisateur reçoit le projet sera assuré de recevoir les nouvelles conversions et n’aura pas modifier des fichiers de bibliothèque.  
  
### <a name="to-extend-the-marshaling-library-with-a-conversion-that-does-not-require-a-context"></a>Pour étendre la bibliothèque de Marshaling avec une Conversion qui ne nécessite pas d’un contexte  
  
1.  Créer un fichier pour stocker les nouvelles fonctions de marshaling, par exemple, MyMarshal.h.  
  
2.  Inclure un ou plusieurs fichiers bibliothèque marshal :  
  
    -   Marshal.h pour les types de base.  
  
    -   marshal_windows.h pour les types de données windows.  
  
    -   marshal_cppstd.h pour les types de données de bibliothèque C++ Standard.  
  
    -   marshal_atl.h pour les types de données ATL.  
  
3.  Utilisez le code à la fin de ces étapes pour écrire la fonction de conversion. Dans ce code, TO est le type à convertir, FROM est le type à partir duquel la conversion et `from` est le paramètre à convertir.  
  
4.  Remplacez le commentaire sur la logique de conversion par du code pour convertir le `from` paramètre dans un objet d’à taper et retourner l’objet converti.  
  
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
  
### <a name="to-extend-the-marshaling-library-with-a-conversion-that-requires-a-context"></a>Pour étendre la bibliothèque de Marshaling avec une Conversion qui nécessite un contexte  
  
1.  Créer un fichier pour stocker les nouvelles fonctions de marshaling, par exemple, MyMarshal.h  
  
2.  Inclure un ou plusieurs fichiers bibliothèque marshal :  
  
    -   Marshal.h pour les types de base.  
  
    -   marshal_windows.h pour les types de données windows.  
  
    -   marshal_cppstd.h pour les types de données de bibliothèque C++ Standard.  
  
    -   marshal_atl.h pour les types de données ATL.  
  
3.  Utilisez le code à la fin de ces étapes pour écrire la fonction de conversion. Dans ce code, TO est le type à convertir, FROM est le type à convertir à partir, `toObject` est un pointeur dans lequel stocker le résultat, et `fromObject` est le paramètre à convertir.  
  
4.  Remplacez le commentaire sur l’initialisation par du code pour initialiser le `toPtr` à la valeur vide appropriée. Par exemple, si elle est un pointeur, affectez-lui la valeur `NULL`.  
  
5.  Remplacez le commentaire sur la logique de conversion par du code pour convertir le `from` paramètre dans un objet de *à* type. Cet objet converti sera stocké dans `toPtr`.  
  
6.  Remplacez le commentaire sur la configuration `toObject` avec le code pour définir `toObject` à votre objet converti.  
  
7.  Remplacez le commentaire sur le nettoyage des ressources natives par du code pour libérer de la mémoire allouée par `toPtr`. Si `toPtr` à l’aide de la mémoire allouée `new`, utilisez `delete` pour libérer la mémoire.  
  
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
  
## <a name="example"></a>Exemple  
 L’exemple suivant étend la bibliothèque de marshaling avec une conversion ne nécessitant pas d’un contexte. Dans cet exemple, le code convertit les informations sur les employés à partir d’un type de données natif en un type de données managées.  
  
```  
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
  
 Dans l’exemple précédent, le `marshal_as` fonction retourne un handle vers les données converties. Cela a été effectuée afin d’éviter la création d’une copie supplémentaire des données. Retourner la variable directement aurait ont un coût de performances inutiles associés.  
  
```Output  
Managed name: Jeff Smith  
Managed address: 123 Main Street  
Managed zip code: 98111  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant convertit les informations sur les employés à partir d’un type de données managées à un type de données natif. Cette conversion nécessite un contexte de marshaling.  
  
```  
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