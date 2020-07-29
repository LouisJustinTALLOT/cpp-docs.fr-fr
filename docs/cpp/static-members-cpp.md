---
title: Membres statiques (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- class members [C++], static
- instance constructors, static members
- class members [C++], shared
- members [C++], static data members
- static members [C++], data members
- static data members [C++]
- data members [C++], static data members
- class instances [C++], shared members
- instance constructors, shared members
- class instances [C++], static members
ms.assetid: 9cc8cf0f-d74c-46f2-8e83-42d4e42c8370
ms.openlocfilehash: b79b65ab3cbf4565f31ad6717f8163c678697c9c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213188"
---
# <a name="static-members-c"></a>Membres statiques (C++)

Les classes peuvent contenir des données membres et des fonctions membres statiques. Quand un membre de données est déclaré comme **`static`** , une seule copie des données est conservée pour tous les objets de la classe.

Les données membres statiques ne font pas partie des objets d'un type donné de classe. Par conséquent, la déclaration de données membres statiques n'est pas considérée comme une définition. Les données membres sont déclarées dans la portée de classe, mais la définition est exécutée au niveau de la portée de fichier. Ces membres statiques ont une liaison externe. L'exemple suivant illustre ce mécanisme :

```cpp
// static_data_members.cpp
class BufferedOutput
{
public:
   // Return number of bytes written by any object of this class.
   short BytesWritten()
   {
      return bytecount;
   }

   // Reset the counter.
   static void ResetCount()
   {
      bytecount = 0;
   }

   // Static member declaration.
   static long bytecount;
};

// Define bytecount in file scope.
long BufferedOutput::bytecount;

int main()
{
}
```

Dans le code précédent, le membre `bytecount` est déclaré dans la classe `BufferedOutput`, mais doit être défini en dehors de la déclaration de classe.

Les données membres statiques peuvent être mentionnées sans faire référence à un objet de type classe. Le nombre d'octets écrits avec des objets `BufferedOutput` peut être obtenu comme suit : 

```cpp
long nBytes = BufferedOutput::bytecount;
```

Pour que le membre statique existe, il n'est pas nécessaire que des objets du type classe existent. Les membres statiques sont également accessibles à l’aide de la sélection de membres (**.** **->** opérateurs and). Par exemple :

```cpp
BufferedOutput Console;

long nBytes = Console.bytecount;
```

Dans le cas précédent, la référence à l'objet (`Console`) n'est pas évaluée ; la valeur retournée est celle de l'objet statique `bytecount`.

Les données membres statiques étant soumises à des règles d'accès de membre de classe, l'accès privé à ces données est autorisé uniquement pour les fonctions membres de classe et friend. Ces règles sont décrites dans [Access Control membres](../cpp/member-access-control-cpp.md). L'exception est que les données membres statiques doivent être définies dans la portée de fichier quelles que soient les restrictions d'accès. Si les données membres doivent être explicitement initialisées, un initialiseur doit être fourni avec la définition.

Le type d'un membre statique n'est pas qualifié par son nom de classe. Par conséquent, le type de `BufferedOutput::bytecount` est **`long`** .

## <a name="see-also"></a>Voir aussi

[Classes et structs](../cpp/classes-and-structs-cpp.md)
