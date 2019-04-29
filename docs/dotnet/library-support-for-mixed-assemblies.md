---
title: Prise en charge de bibliothèque pour les assemblys mixtes
ms.date: 09/18/2018
helpviewer_keywords:
- msvcm90[d].dll
- mixed assemblies [C++], library support
- msvcmrt[d].lib
- libraries [C++], mixed assemblies
ms.assetid: 1229595c-9e9d-414d-b018-b4e4c727576d
ms.openlocfilehash: 42116c09d5b31cf669eb6d5d1e75eae60b2610a7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62312006"
---
# <a name="library-support-for-mixed-assemblies"></a>Prise en charge de bibliothèque pour les assemblys mixtes

Visual C++ prend en charge l’utilisation de la bibliothèque Standard C++, la bibliothèque de runtime C (CRT), ATL et MFC pour les applications compilées avec [/clr (Compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md). Ainsi, les applications existantes qui utilisent ces bibliothèques à utiliser également les fonctionnalités de .NET Framework.

> [!IMPORTANT]
> Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

Cette prise en charge inclut les bibliothèques DLL et d’importation suivantes :

- Msvcmrt [d] .lib si vous compilez avec **/CLR**. Lien d’assemblys mixtes vers cette bibliothèque d’importation.

Cette prise en charge offre que plusieurs avantages connexes :

- La bibliothèque CRT et la bibliothèque C++ Standard sont disponibles pour le code mixte. La bibliothèque CRT et la bibliothèque C++ Standard fournis ne sont pas vérifiables ; au final, vos appels sont toujours acheminés vers le CRT et la bibliothèque C++ Standard même que celles que vous utilisez à partir du code natif.

- Unifiée de gestion des exceptions dans les images mixtes.

- Initialisation statique de variables C++ dans les images mixtes.

- Prise en charge pour les variables par processus et par domaine d’application dans le code managé.

- Résout les problèmes de verrouillage du chargeur appliqués aux DLL mixtes compilés dans Visual Studio 2003 et versions antérieures.

En outre, cette prise en charge présente les limitations suivantes :

- Uniquement le modèle de la DLL CRT est pris en charge pour le code compilé avec **/CLR**. Aucune bibliothèque CRT statique qui prennent en charge **/CLR** génère.

## <a name="see-also"></a>Voir aussi

- [Assemblys mixtes (natif et managé)](../dotnet/mixed-native-and-managed-assemblies.md)
