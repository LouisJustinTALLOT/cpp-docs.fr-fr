---
title: Conversion de projets du mode mixte en langage intermédiaire pur
ms.date: 08/19/2019
helpviewer_keywords:
- intermediate language, mixed-mode applications
- mixed-mode applications
- mixed-mode applications, intermediate language
- projects [C++], converting to intermediate language
ms.assetid: 855f9e3c-4f09-4bfe-8eab-a45f68292be9
ms.openlocfilehash: 05ece23e6d79fc399085099deebcde0aa4a92c64
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2019
ms.locfileid: "70311625"
---
# <a name="converting-projects-from-mixed-mode-to-pure-intermediate-language"></a>Conversion de projets du mode mixte en langage intermédiaire pur

Tous les C++ projets CLR Visual sont liés aux bibliothèques Runtime C par défaut. Par conséquent, ces projets sont classés en tant qu’applications en mode mixte, car ils combinent du code natif avec du code qui cible le common language runtime (code managé). Lorsqu’elles sont compilées, elles sont compilées en langage intermédiaire (IL), également connu sous le nom de langage MSIL (Microsoft Intermediate Language).

> [!IMPORTANT]
> Visual Studio 2015 déconseillé et Visual Studio 2017 ne prend plus en charge la création de code **/clr : pure** ou **/clr : safe** pour les applications CLR. Si vous avez besoin d’assemblys purs ou sécurisés, nous vous recommandons de C#traduire votre application en.

Si vous utilisez une version antérieure de l’ensemble d' C++ outils du compilateur Microsoft qui prend en charge **/clr : pure** ou **/clr : safe**, vous pouvez utiliser cette procédure pour convertir votre code en MSIL pur :

### <a name="to-convert-your-mixed-mode-application-into-pure-intermediate-language"></a>Pour convertir votre application en mode mixte en langage intermédiaire pur

1. Supprimer les liens vers les [bibliothèques Runtime C](../c-runtime-library/crt-library-features.md) (CRT) :

   1. Dans le fichier. cpp définissant le point d’entrée de votre application, remplacez le point `Main()`d’entrée par. L' `Main()` utilisation de indique que votre projet n’est pas lié au CRT.

   2. Dans Explorateur de solutions, cliquez avec le bouton droit sur votre projet et sélectionnez **Propriétés** dans le menu contextuel pour ouvrir les pages de propriétés de votre application.

   3. Dans la page de propriétés projet **avancé** de l' **éditeur de liens**, sélectionnez le point d' **entrée** , puis entrez **main** dans ce champ.

   4. Pour les applications console, dans la page de propriétés projet **système** de l' **éditeur de liens**, sélectionnez le champ **sous-système** et remplacez-le par **console (/SUBSYSTEM : console)** .

      > [!NOTE]
      > Vous n’avez pas besoin de définir cette propriété pour Windows Forms applications, car le champ **sous-système** est défini sur **Windows (/SUBSYSTEM : Windows)** par défaut.

   5. Dans *stdafx. h*, commentez toutes les `#include` instructions. Par exemple, dans les applications console :

      ```cpp
      // #include <iostream>
      // #include <tchar.h>
      ```

       \- ou -

       Par exemple, dans les applications Windows Forms :

      ```cpp
      // #include <stdlib.h>
      // #include <malloc.h>
      // #include <memory.h>
      // #include <tchar.h>
      ```

   6. Pour les applications Windows Forms, dans Form1. cpp, commentez `#include` l’instruction qui fait référence à Windows. h. Par exemple :

      ```cpp
      // #include <windows.h>
      ```

2. Ajoutez le code suivant à *stdafx. h*:

   ```cpp
   #ifndef __FLTUSED__
   #define __FLTUSED__
      extern "C" __declspec(selectany) int _fltused=1;
   #endif
   ```

3. Supprimer tous les types non managés :

   Le cas échéant, remplacez les types non managés par des références aux structures de l’espace de noms [System](/dotnet/api/system) . Les types managés courants sont répertoriés dans le tableau suivant :

   |Structure|Description|
   |---------------|-----------------|
   |[Boolean](/dotnet/api/system.boolean)|Représente une valeur booléenne.|
   |[Byte](/dotnet/api/system.byte)|Représente un entier non signé 8 bits.|
   |[Char](/dotnet/api/system.char)|Représente un caractère Unicode.|
   |[DateTime](/dotnet/api/system.datetime)|Représente un instant, généralement exprimé sous la forme d'une date et d'une heure.|
   |[Decimal](/dotnet/api/system.decimal)|Représente un nombre décimal.|
   |[Double](/dotnet/api/system.double)|Représente un nombre à virgule flottante double précision.|
   |[Guid](/dotnet/api/system.guid)|Représente un GUID (identificateur global unique).|
   |[Int16](/dotnet/api/system.int16)|Représente un entier signé 16 bits.|
   |[Int32](/dotnet/api/system.int32)|Représente un entier signé 32 bits.|
   |[Int64](/dotnet/api/system.int64)|Représente un entier signé 64 bits.|
   |[IntPtr](/dotnet/api/system.intptr)|Type spécifique à la plateforme, utilisé pour représenter un pointeur ou un handle.|
   |[SByte](/dotnet/api/system.byte)|Représente un entier 8 bits signé.|
   |[Single](/dotnet/api/system.single)|Représente un nombre à virgule flottante simple précision.|
   |[TimeSpan](/dotnet/api/system.timespan)|Représente un intervalle de temps.|
   |[UInt16](/dotnet/api/system.uint16)|Représente un entier non signé 16 bits.|
   |[UInt32](/dotnet/api/system.uint32)|Représente un entier non signé 32 bits.|
   |[UInt64](/dotnet/api/system.uint64)|Représente un entier non signé 64 bits.|
   |[UIntPtr](/dotnet/api/system.uintptr)|Type spécifique à la plateforme, utilisé pour représenter un pointeur ou un handle.|
   |[Void](/dotnet/api/system.void)|Indique une méthode qui ne retourne pas de valeur ; autrement dit, la méthode a le type de retour void.|