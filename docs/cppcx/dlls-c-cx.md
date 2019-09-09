---
title: DLL (C++/CX)
ms.date: 02/06/2018
ms.assetid: 5b8bcc57-64dd-4c54-9f24-26a25bd5dddd
ms.openlocfilehash: 4db0ed4f11f03c65c440c7b654653347da1d4536
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740272"
---
# <a name="dlls-ccx"></a>DLL (C++/CX)

Vous pouvez utiliser Visual Studio pour créer une DLL Win32 standard ou une DLL de composant Windows Runtime qui peut être consommée par les applications plateforme Windows universelle (UWP). Une DLL standard qui a été créée à l’aide d’une version de Visual Studio C++ ou du compilateur Microsoft antérieure à Visual Studio 2012 peut ne pas se charger correctement dans une application UWP et risque de ne pas réussir le test de vérification de l’application dans le Microsoft Store.

## <a name="windows-runtime-component-dlls"></a>Dll du composant Windows Runtime

Dans presque tous les cas, lorsque vous souhaitez créer une DLL à utiliser dans une application UWP, créez-la en tant que composant Windows Runtime à l’aide du modèle de projet de ce nom. Vous pouvez créer un projet de composant Windows Runtime pour les dll qui ont des types de Windows Runtime publics ou privés. Vous pouvez accéder à un composant Windows Runtime à partir d’applications écrites dans n’importe quel langage compatible Windows Runtime. Par défaut, les paramètres du compilateur pour un projet de composant Windows Runtime utilisent le commutateur **/ZW** Un fichier .winmd doit avoir le même nom que l'espace de noms racine. Par exemple, une classe nommée A.B.C.MyClass peut être instanciée uniquement si elle est définie dans un fichier de métadonnées nommé A.winmd, A.B.winmd ou A.B.C.winmd. Il n'est pas requis que le nom de la DLL corresponde au nom du fichier .winmd.

Pour plus d'informations, consultez [Creating Windows Runtime Components in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

### <a name="to-reference-a-third-party-windows-runtime-component-binary-in-your-project"></a>Pour référencer un fichier binaire de composant Windows Runtime tiers dans votre projet

1. Ouvrez le menu contextuel du projet qui utilisera la DLL puis choisissez **Propriétés**. Dans la page **Propriétés communes** , choisissez le bouton **Ajouter une nouvelle référence** .

1. Un composant Windows Runtime se compose d’un fichier DLL et d’un fichier. winmd qui contient les métadonnées. En général, ces fichiers se trouvent dans le même répertoire. Dans le volet gauche de la boîte de dialogue **Ajouter une référence** , choisissez le bouton **Parcourir** puis accédez à l'emplacement de la DLL et de son fichier .winmd. Pour plus d’informations, consultez [Kits de développement](/visualstudio/extensibility/creating-a-software-development-kit#extension-sdks)logiciel (SDK) d’extension.

## <a name="standard-dlls"></a>DLL standard

Vous pouvez créer une DLL standard pour C++ du code qui ne consomme pas ou ne produit pas de types de Windows Runtime public et les consomme à partir d’une application UWP. Utilisez le type de projet de bibliothèque de liens dynamiques (DLL) lorsque vous souhaitez simplement migrer une DLL existante à compiler dans cette version de Visual Studio, mais ne convertissez pas le code en projet de composant Windows Runtime. En utilisant la procédure suivante, la DLL sera déployée à côté de l'exécutable de votre application dans le package .appx.

### <a name="to-create-a-standard-dll-in-visual-studio"></a>Pour créer une DLL standard dans Visual Studio

1. Dans la barre de menus, choisissez **fichier**, **nouveau**, **projet**, puis sélectionnez le modèle **bibliothèque de liens dynamiques (dll)** .

1. Entrez un nom pour le projet, puis choisissez le bouton **OK** .

1. Ajoutez le code. Veillez à utiliser `__declspec(dllexport)` pour les fonctions que vous prévoyez d'exporter, par exemple `__declspec(dllexport) Add(int I, in j);`

1. Ajoutez `#include winapifamily.h` pour inclure ce fichier d’en-tête à partir de la SDK Windows pour les `WINAPI_FAMILY=WINAPI_PARTITION_APP`applications UWP et définissez la macro.

### <a name="to-reference-a-standard-dll-project-from-the-same-solution"></a>Référencement d'un projet DLL standard à partir de la même solution

1. Ouvrez le menu contextuel du projet qui utilisera la DLL puis choisissez **Propriétés**. Dans la page **Propriétés communes** , choisissez le bouton **Ajouter une nouvelle référence** .

1. Dans le volet gauche, sélectionnez **Solution**, puis activez la case à cocher appropriée dans le volet droit.

1. Dans vos fichiers de code source, ajoutez une instruction `#include` pour le fichier d'en-tête de DLL selon vos besoins.

### <a name="to-reference-a-standard-dll-binary"></a>Référencement d'un fichier binaire de DLL standard

1. Copiez le fichier DLL, le fichier .lib et le fichier d'en-tête, puis collez-les dans un emplacement connu, par exemple dans votre dossier de projet actif.

1. Ouvrez le menu contextuel du projet qui utilisera la DLL puis choisissez **Propriétés**. Dans la page **Propriétés de configuration**, **Éditeur de liens**, **Entrée** , ajoutez le fichier .lib comme dépendance.

1. Dans vos fichiers de code source, ajoutez une instruction `#include` pour le fichier d'en-tête de DLL selon vos besoins.

### <a name="to-migrate-an-existing-win32-dll-for-uwp-app-compatibility"></a>Pour migrer une DLL Win32 existante pour la compatibilité des applications UWP

1. Créez un projet de type DLL (Windows universel) et ajoutez-y votre code source existant.

1. Ajoutez `#include winapifamily.h` pour inclure ce fichier d’en-tête à partir de la SDK Windows pour les `WINAPI_FAMILY=WINAPI_PARTITION_APP`applications UWP et définissez la macro.

1. Dans vos fichiers de code source, ajoutez une instruction `#include` pour le fichier d'en-tête de DLL selon vos besoins.
