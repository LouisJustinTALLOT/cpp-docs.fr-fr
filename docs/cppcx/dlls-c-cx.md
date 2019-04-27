---
title: DLL (C++/CX)
ms.date: 02/06/2018
ms.assetid: 5b8bcc57-64dd-4c54-9f24-26a25bd5dddd
ms.openlocfilehash: 1a72ecc5eb46abfbc7b9a52a168510ce0873ee04
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62183275"
---
# <a name="dlls-ccx"></a>DLL (C++/CX)

Vous pouvez utiliser Visual Studio pour créer une DLL Win32 standard ou un composant Windows Runtime DLL qui peut être utilisé par les applications Universal Windows Platform (UWP). Une DLL standard qui a été créée à l’aide d’une version de Visual Studio ou le compilateur Visual C++ antérieure à Visual Studio 2012 ne se charge pas correctement dans une application UWP et peut ne pas passer le test de vérification d’application dans le Microsoft Store.

## <a name="windows-runtime-component-dlls"></a>DLL des composants Windows Runtime

Dans presque tous les cas, lorsque vous souhaitez créer une DLL pour les utiliser dans une application UWP, créez-la comme un composant Windows Runtime en utilisant le modèle de projet portant ce nom. Vous pouvez créer un projet de composant Windows Runtime pour les DLL qui ont des types Windows Runtime publics ou privés. Un composant Windows Runtime sont accessibles à partir d’applications qui sont écrits dans n’importe quel langage compatible avec Windows Runtime. Par défaut, les paramètres de compilateur pour un composant Windows Runtime projet utiliser les **/ZW** basculer. Un fichier .winmd doit avoir le même nom que l'espace de noms racine. Par exemple, une classe nommée A.B.C.MyClass peut être instanciée uniquement si elle est définie dans un fichier de métadonnées nommé A.winmd, A.B.winmd ou A.B.C.winmd. Il n'est pas requis que le nom de la DLL corresponde au nom du fichier .winmd.

Pour plus d'informations, consultez [Creating Windows Runtime Components in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

### <a name="to-reference-a-third-party-windows-runtime-component-binary-in-your-project"></a>Pour référencer un composant de Windows Runtime tiers binaire dans votre projet

1. Ouvrez le menu contextuel du projet qui utilisera la DLL puis choisissez **Propriétés**. Dans la page **Propriétés communes** , choisissez le bouton **Ajouter une nouvelle référence** .

1. Un composant Windows Runtime se compose d’un fichier DLL et un fichier .winmd qui contient les métadonnées. En général, ces fichiers se trouvent dans le même répertoire. Dans le volet gauche de la boîte de dialogue **Ajouter une référence** , choisissez le bouton **Parcourir** puis accédez à l'emplacement de la DLL et de son fichier .winmd. Pour plus d’informations, consultez [SDK d’Extension](/visualstudio/extensibility/creating-a-software-development-kit#ExtensionSDKs).

## <a name="standard-dlls"></a>DLL standard

Vous pouvez créer une DLL standard pour le code C++ qui ne consomment ou produisent des types Windows Runtime publiques et le consommer à partir d’une application UWP. Utilisez le type de projet de bibliothèque de liens dynamiques (DLL) lorsque vous souhaitez juste migrer une DLL existante pour les compiler dans cette version de Visual Studio, mais pas convertir le code à un projet de composant d’exécution de Windows. En utilisant la procédure suivante, la DLL sera déployée à côté de l'exécutable de votre application dans le package .appx.

### <a name="to-create-a-standard-dll-in-visual-studio"></a>Pour créer une DLL standard dans Visual Studio

1. Dans la barre de menus, choisissez **fichier**, **New**, **projet**, puis sélectionnez le **bibliothèque de liens dynamiques (DLL)** modèle.

1. Entrez un nom pour le projet, puis choisissez le bouton **OK** .

1. Ajoutez le code. Veillez à utiliser `__declspec(dllexport)` pour les fonctions que vous prévoyez d'exporter, par exemple `__declspec(dllexport) Add(int I, in j);`

1. Ajouter `#include winapifamily.h` pour inclure ce fichier d’en-tête à partir du SDK Windows pour les applications UWP et de définir la macro `WINAPI_FAMILY=WINAPI_PARTITION_APP`.

### <a name="to-reference-a-standard-dll-project-from-the-same-solution"></a>Référencement d'un projet DLL standard à partir de la même solution

1. Ouvrez le menu contextuel du projet qui utilisera la DLL puis choisissez **Propriétés**. Dans la page **Propriétés communes** , choisissez le bouton **Ajouter une nouvelle référence** .

1. Dans le volet gauche, sélectionnez **Solution**, puis activez la case à cocher appropriée dans le volet droit.

1. Dans vos fichiers de code source, ajoutez une instruction `#include` pour le fichier d'en-tête de DLL selon vos besoins.

### <a name="to-reference-a-standard-dll-binary"></a>Référencement d'un fichier binaire de DLL standard

1. Copiez le fichier DLL, le fichier .lib et le fichier d'en-tête, puis collez-les dans un emplacement connu, par exemple dans votre dossier de projet actif.

1. Ouvrez le menu contextuel du projet qui utilisera la DLL puis choisissez **Propriétés**. Dans la page **Propriétés de configuration**, **Éditeur de liens**, **Entrée** , ajoutez le fichier .lib comme dépendance.

1. Dans vos fichiers de code source, ajoutez une instruction `#include` pour le fichier d'en-tête de DLL selon vos besoins.

### <a name="to-migrate-an-existing-win32-dll-for-uwp-app-compatibility"></a>Pour migrer une DLL Win32 existante pour la compatibilité des applications UWP

1. Créez un projet du type DLL (Windows universel) et ajoutez votre code source existant à ce dernier.

1. Ajouter `#include winapifamily.h` pour inclure ce fichier d’en-tête à partir du SDK Windows pour les applications UWP et de définir la macro `WINAPI_FAMILY=WINAPI_PARTITION_APP`.

1. Dans vos fichiers de code source, ajoutez une instruction `#include` pour le fichier d'en-tête de DLL selon vos besoins.
