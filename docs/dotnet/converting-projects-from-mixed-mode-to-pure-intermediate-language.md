---
title: Conversion de projets du mode mixte en langage intermédiaire pur
ms.date: 11/04/2016
helpviewer_keywords:
- intermediate language, mixed-mode applications
- mixed-mode applications
- mixed-mode applications, intermediate language
- projects [C++], converting to intermediate language
ms.assetid: 855f9e3c-4f09-4bfe-8eab-a45f68292be9
ms.openlocfilehash: 2f63b6860157e315d44f7c050812a7f0b97f2726
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65448041"
---
# <a name="converting-projects-from-mixed-mode-to-pure-intermediate-language"></a>Conversion de projets du mode mixte en langage intermédiaire pur

Tous les projets Visual C++ CLR lier aux bibliothèques C Runtime par défaut. Par conséquent, ces projets sont classés en tant qu’applications en mode mixte, car elles combinent le code natif avec du code qui cible le common language runtime (code managé). Quand elles sont compilées, elles sont compilées en langage intermédiaire (IL), également connu sous Microsoft intermediate language (MSIL).

> [!IMPORTANT]
> Déconseillé de Visual Studio 2015 et Visual Studio 2017 prend n’est plus en charge la création de **/CLR : pure** ou **/CLR : safe** code pour les applications CLR. Si vous avez besoin des assemblys pures ou safe, nous vous recommandons de que vous traduisez votre application en c#.

Si vous utilisez une version antérieure de Microsoft C++ ensemble d’outils du compilateur qui prend en charge **/CLR : pure** ou **/CLR : safe**, vous pouvez utiliser cette procédure pour convertir votre code en MSIL pur :

### <a name="to-convert-your-mixed-mode-application-into-pure-intermediate-language"></a>Pour convertir votre application en mode mixte en langage intermédiaire pur

1. Supprimer les liens vers les [les bibliothèques Runtime C](../c-runtime-library/crt-library-features.md) (CRT) :

   1. Dans le fichier .cpp définissant le point d’entrée de votre application, modifiez le point d’entrée à `Main()`. À l’aide de `Main()` indique que votre projet ne pointe pas vers la bibliothèque CRT.

   2. Dans l’Explorateur de solutions, cliquez sur votre projet et sélectionnez **propriétés** dans le menu contextuel pour ouvrir les pages de propriétés pour votre application.

   3. Dans le **avancé** page de propriétés de projet pour le **l’éditeur de liens**, sélectionnez le **Point d’entrée** , puis entrez **Main** dans ce champ.

   4. Pour les applications de console, dans le **système** page de propriétés de projet pour le **l’éditeur de liens**, sélectionnez le **sous-système** champ et modifier ce paramètre pour **Console (/ SUBSYSTEM:console)**.

      > [!NOTE]
      > Vous n’êtes pas obligé de définir cette propriété pour les applications Windows Forms, car le **sous-système** champ est défini sur **Windows (/ SUBSYSTEM : WINDOWS)** par défaut.

   5. Dans stdafx.h, commentez tout le `#include` instructions. Par exemple, dans les applications de console :

      ```cpp
      // #include <iostream>
      // #include <tchar.h>
      ```

       - ou -

       Par exemple, dans les applications Windows Forms :

      ```cpp
      // #include <stdlib.h>
      // #include <malloc.h>
      // #include <memory.h>
      // #include <tchar.h>
      ```

   6. Pour les applications Windows Forms, dans Form1.cpp, comment la `#include` instruction qui fait référence à windows.h. Exemple :

      ```cpp
      // #include <windows.h>
      ```

2. Ajoutez le code suivant à stdafx.h :

   ```cpp
   #ifndef __FLTUSED__
   #define __FLTUSED__
      extern "C" __declspec(selectany) int _fltused=1;
   #endif
   ```

3. Supprimer tous les types non managés :

   Le cas échéant, remplacez les types non managés avec des références à des structures de la [système](/dotnet/api/system) espace de noms. Les types managés courants sont répertoriés dans le tableau suivant :

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
   |[Void](/dotnet/api/system.void)|Indique une méthode qui ne retourne pas de valeur ; Autrement dit, la méthode a le type de retour void.|