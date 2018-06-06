---
title: Prise en charge pour les assemblys mixtes | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- msvcm90[d].dll
- mixed assemblies [C++], library support
- msvcmrt[d].lib
- libraries [C++], mixed assemblies
ms.assetid: 1229595c-9e9d-414d-b018-b4e4c727576d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d4b584e0bacb1cb93cad33efdff807bb5fa9c8e2
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704109"
---
# <a name="library-support-for-mixed-assemblies"></a>Prise en charge de bibliothèque pour les assemblys mixtes

Visual C++ prend en charge l’utilisation de la bibliothèque C++ Standard, la bibliothèque de runtime C (CRT), ATL et MFC pour les applications compilées avec [/clr (Compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md). Ainsi, les applications existantes qui utilisent ces bibliothèques à utiliser aussi bien les fonctionnalités de .NET Framework.

> [!IMPORTANT]
> Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

Cette prise en charge inclut les bibliothèques DLL et d’importation suivantes :

- Msvcmrt [d] .lib si vous compilez avec **/CLR**. Assemblys mixtes un lien vers cette bibliothèque d’importation.

Cette prise en charge offre que plusieurs avantages connexes :

- Le CRT et la bibliothèque C++ Standard sont disponibles pour le code mixte. Le CRT et la bibliothèque C++ Standard fournis ne sont pas vérifiables ; Finalement, vos appels sont encore routés aux mêmes CRT et bibliothèque C++ Standard que vous utilisez du code natif.

- Corriger la gestion des exceptions unifiée dans les images mixtes.

- Initialisation statique de variables C++ dans les images mixtes.

- Prise en charge pour les variables par processus et par domaine d’application dans le code managé.

- Résout les problèmes de verrouillage du chargeur appliqués aux DLL mixtes compilés dans Visual Studio 2003 et versions antérieures.

En outre, cette prise en charge présente les limitations suivantes :

- Seul le modèle de la DLL CRT est pris en charge pour le code compilé avec **/CLR**. Aucune bibliothèque CRT statique qui prennent en charge **/CLR** génère.

Vous devez mettre à jour votre langage CLR (common runtime) vers la version actuelle comme il n’est pas garanti pour travailler avec les versions antérieures. Code généré avec ces modifications ne s’exécutera pas sur CLR version 1.x.

## <a name="see-also"></a>Voir aussi

- [Assemblys mixtes (natif et managé)](../dotnet/mixed-native-and-managed-assemblies.md)
