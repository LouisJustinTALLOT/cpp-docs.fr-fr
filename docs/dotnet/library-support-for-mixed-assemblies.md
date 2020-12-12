---
description: 'En savoir plus sur : la prise en charge de bibliothèque pour les assemblys mixtes'
title: Prise en charge de bibliothèque pour les assemblys mixtes
ms.date: 09/18/2018
helpviewer_keywords:
- msvcm90[d].dll
- mixed assemblies [C++], library support
- msvcmrt[d].lib
- libraries [C++], mixed assemblies
ms.assetid: 1229595c-9e9d-414d-b018-b4e4c727576d
ms.openlocfilehash: d20069c2caa1cf46ebdb54907de586630d4ee71c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113712"
---
# <a name="library-support-for-mixed-assemblies"></a>Prise en charge de bibliothèque pour les assemblys mixtes

Visual C++ prend en charge l’utilisation de la bibliothèque C++ standard, la bibliothèque Runtime C (CRT), ATL et MFC pour les applications compilées avec [/clr (compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md). Cela permet aux applications existantes qui utilisent ces bibliothèques d’utiliser également les fonctionnalités de .NET Framework.

> [!IMPORTANT]
> Les options de compilateur **/clr : pure** et **/clr : safe** sont dépréciées dans Visual Studio 2015 et ne sont pas prises en charge dans Visual Studio 2017.

Cette prise en charge comprend les bibliothèques DLL et d’importation suivantes :

- Msvcmrt [d]. lib si vous compilez avec **/CLR**. Les assemblys mixtes sont liés à cette bibliothèque d’importation.

Cette prise en charge offre plusieurs avantages connexes :

- La bibliothèque standard CRT et C++ est disponible pour le code mixte. La bibliothèque standard CRT et C++ fournie ne sont pas vérifiables ; Enfin, vos appels sont toujours acheminés vers la même bibliothèque CRT et la même bibliothèque standard C++ que vous utilisez à partir du code natif.

- Corriger la gestion unifiée des exceptions dans les images mixtes.

- Initialisation statique des variables C++ dans les images mixtes.

- Prise en charge des variables par AppDomain et par processus dans du code managé.

- Résout les problèmes de verrouillage du chargeur qui ont été appliqués aux DLL mixtes compilées dans Visual Studio 2003 et versions antérieures.

En outre, cette prise en charge présente les limitations suivantes :

- Seul le modèle de DLL CRT est pris en charge pour le code compilé avec **/CLR**. Il n’existe aucune bibliothèque CRT statique prenant en charge les builds **/CLR** .

## <a name="see-also"></a>Voir aussi

- [Assemblys mixtes (natifs et managés)](../dotnet/mixed-native-and-managed-assemblies.md)
