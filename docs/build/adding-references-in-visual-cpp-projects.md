---
title: Utilisation de bibliothèques et de composants dans des projets C++
ms.date: 12/10/2018
f1_keywords:
- VC.Project.References
helpviewer_keywords:
- Add References Dialog Box (C++)
- .NET Framework (C++), Add References Dialog Box
ms.assetid: 12b8f571-0f21-40b3-9404-5318a57e9cb5
ms.openlocfilehash: 37c0120b7879678ad65dfbbffc17bd6d6791fdfe
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229907"
---
# <a name="consuming-libraries-and-components"></a>Utilisation de bibliothèques et de composants

Souvent, un projet C++ doit appeler des fonctions ou accéder aux données dans un fichier binaire, tel qu’une bibliothèque statique (fichiers. lib), une DLL, un composant Windows Runtime, un composant COM ou un assembly .NET. Dans ce cas, vous devez configurer le projet afin qu’il puisse trouver ce fichier binaire au moment de la génération. Les étapes spécifiques dépendent du type de votre projet, du type de fichier binaire et de l’éventuelle génération du fichier binaire dans la même solution que votre projet.

## <a name="consuming-libraries-downloaded-via-vcpkg"></a>Utilisation de bibliothèques téléchargées via vcpkg

Pour utiliser une bibliothèque que vous avez téléchargée à l’aide du gestionnaire de package **vcpkg** , vous pouvez ignorer les instructions ci-dessous. Pour plus d’informations [, consultez vcpkg : gestionnaire de package C++ pour Windows, Linux et MacOS](vcpkg.md#integrate-with-visual-studio-windows) .

## <a name="consuming-static-libraries"></a>Utilisation de bibliothèques statiques

Si votre projet de bibliothèque statique est généré dans la même solution :

1. #<a name="include-the-header-files-for-the-static-library-using-quotation-marks-in-a-typical-solution-the-path-will-start-with-library-project-name-intellisense-will-help-you-find-it"></a>incluez le ou les fichiers d’en-tête pour la bibliothèque statique à l’aide de guillemets. Dans une solution standard, le chemin d’accès commence par `../<library project name>` . IntelliSense vous aide à le trouver.
2. Ajoutez une référence au projet de bibliothèque statique. Cliquez avec le bouton droit sur **références** sous le nœud projet d’application dans **Explorateur de solutions** et choisissez **Ajouter une référence**.

Si la bibliothèque statique ne fait pas partie de la solution :

1. Dans **Explorateur de solutions** , cliquez avec le bouton droit sur le nœud du projet d’application, puis choisissez **Propriétés**.
2. Dans la page de propriétés **Répertoires VC + +** , ajoutez le chemin d’accès au répertoire où se trouve le fichier. lib dans les **chemins d’accès de bibliothèque** , puis ajoutez le chemin d’accès au (x) fichier (s) d’en-tête de bibliothèque dans les **répertoires Include**.  
3. Dans l' **éditeur de liens >** page de propriétés d’entrée, ajoutez le nom du fichier. lib aux **dépendances supplémentaires**.

## <a name="dynamic-link-libraries"></a>Bibliothèques de liens dynamiques

Si la DLL est générée dans le cadre de la même solution que l’application, suivez les mêmes étapes que pour une bibliothèque statique.

Si la DLL ne fait pas partie de la solution d’application, vous avez besoin du fichier DLL, des en-têtes avec des prototypes pour les fonctions et les classes exportées, et d’un fichier. lib qui fournit les informations de liaison nécessaires.

1. Copiez la DLL dans le dossier de sortie de votre projet ou dans un autre dossier du chemin d’accès de recherche Windows standard pour les dll. Consultez l' [ordre de recherche de la bibliothèque de liens dynamiques](/windows/win32/dlls/dynamic-link-library-search-order).
2. Suivez les étapes 1-3 pour les bibliothèques statiques pour fournir les chemins d’accès aux en-têtes et au fichier. lib.

## <a name="com-objects"></a>objets COM

Si votre application C++ native doit consommer un objet COM et que cet objet est *inscrit*, il vous suffit d’appeler CoCreateInstance et de transmettre le CLSID de l’objet. Le système le trouvera dans le Registre Windows et le chargera. Un projet C++/CLI peut consommer un objet COM de la même manière, ou en ajoutant une référence à partir de la liste **Ajouter des références > com** et en l’utilisant via son [Wrapper pouvant être appelé](/dotnet/framework/interop/runtime-callable-wrapper)par le Runtime.

## <a name="net-assemblies-and-windows-runtime-components"></a>Assemblys .NET et composants de Windows Runtime

Dans les projets UWP ou C++/CLI, vous consommez des assemblys .NET ou des composants Windows Runtime en ajoutant une *référence* à l’assembly ou au composant. Sous le nœud **références** dans un projet UWP ou C++/CLI, vous voyez des références à des composants couramment utilisés. Cliquez avec le bouton droit sur le nœud **références** dans **Explorateur de solutions** pour afficher le **Gestionnaire de références** et parcourir les autres composants connus du système. Cliquez sur le bouton **Parcourir** pour accéder à un dossier où se trouve un composant personnalisé. Étant donné que les assemblys .NET et les composants Windows Runtime contiennent des informations de type intégrées, vous pouvez afficher leurs méthodes et classes en cliquant avec le bouton droit et en sélectionnant **afficher dans l’Explorateur d’objets**.

## <a name="reference-properties"></a>Propriétés de référence

Chaque genre de référence possède des propriétés. Pour afficher les propriétés, sélectionnez la référence dans l’Explorateur de solutions et appuyez sur **Alt+Entrée**, ou cliquez avec le bouton droit et choisissez **Propriétés**. Certaines propriétés sont en lecture seule, et d’autres peuvent être modifiées. Toutefois, en règle générale, vous n’avez pas à modifier ces propriétés manuellement.

### <a name="activex-reference-properties"></a>Propriétés de référence ActiveX

Les propriétés de référence ActiveX sont disponibles uniquement pour les références aux composants COM. Ces propriétés sont affichées uniquement quand un composant COM est sélectionné dans le volet **Références** . Les propriétés ne peuvent pas être modifiées.

- **Chemin d’accès complet du contrôle**

   Affiche le chemin d'accès du répertoire du contrôle référencé.

- **GUID du contrôle**

   Affiche le GUID du contrôle ActiveX.

- **Version de contrôle**

   Affiche la version du contrôle ActiveX référencé.

- **Nom de la bibliothèque de types**

   Affiche le nom de la bibliothèque de types référencée.

- **Outil wrapper**

   Affiche l'outil utilisé pour générer l'assembly d'interopérabilité à partir de la bibliothèque COM référencée ou d'un contrôle ActiveX.

### <a name="assembly-reference-properties-ccli"></a>Propriétés de référence de l’assembly (C++/CLI)

Les propriétés de référence d’assembly sont disponibles uniquement pour les références aux assemblys .NET Framework dans les projets C++/CLI. Ces propriétés s’affichent uniquement lorsqu’un assembly de .NET Framework est sélectionné dans le volet **références** . Les propriétés ne peuvent pas être modifiées.

- **Chemin d’accès relatif**

   Affiche le chemin d'accès relatif du répertoire de projet à l'assembly référencé.

### <a name="build-properties"></a>Propriétés de la build

Les propriétés suivantes sont disponibles sur divers genres de références. Elles vous permettent de spécifier le mode de génération avec des références.

- **Copie locale**

   Spécifie si l'assembly référencé doit être copié automatiquement vers l'emplacement cible pendant une génération.

- **Copier les assemblys satellites locaux (C++/CLI)**

   Spécifie si les assemblys satellites de l'assembly référencé doivent être copiés automatiquement vers l'emplacement cible pendant une génération. Utilisé uniquement si **copie locale** est **`true`** .

- **Sortie de l’assembly de référence**

   Spécifie que cet assembly est utilisé dans le processus de génération. Si **`true`** , l’assembly est utilisé sur la ligne de commande du compilateur pendant la génération.

### <a name="project-to-project-reference-properties"></a>Propriétés de référence entre projets

Les propriétés suivantes définissent une *référence* entre projets à partir du projet sélectionné dans le volet **références** vers un autre projet de la même solution. Pour plus d’informations, consultez [Gestion des références dans un projet](/visualstudio/ide/managing-references-in-a-project).

- **Lier les dépendances de la bibliothèque**

   Quand cette propriété a la valeur **True**, le système de projet lie au projet dépendant les fichiers .lib produits par le projet indépendant. En général, vous devez spécifier **True**.

- **Identificateur de projet**

   Identifie de façon unique le projet indépendant. La valeur de propriété est un GUID système interne qui ne peut pas être modifié.

- **Utiliser les entrées de dépendance de la bibliothèque**

   Quand cette propriété a la valeur **False**, le système de projet ne lie pas au projet dépendant les fichiers .obj de la bibliothèque produite par le projet indépendant. Ainsi, cette valeur désactive la liaison incrémentielle. En général, vous spécifiez **False** , car la génération de l'application peut prendre du temps, s'il existe de nombreux projets indépendants.

### <a name="read-only-reference-properties-com--net"></a>Propriétés de référence en lecture seule (COM & .NET)

Les propriétés suivantes font partie des références d’assembly COM et .NET. Elles ne peuvent pas être modifiées.

- **Nom de l’assembly**

   Affiche le nom de l'assembly pour l'assembly référencé.

- **Culture**

   Affiche la culture de la référence sélectionnée.

- **Description**

   Affiche la description de la référence sélectionnée.

- **Chemin d'accès complet**

   Affiche le chemin d'accès du répertoire de l'assembly référencé.

- **Identité**

   Pour les assemblys .NET Framework, affiche le chemin complet. Pour les composants COM, affiche le GUID.

- **Étiquette**

   Affiche l'étiquette de la référence.

- **Nom**

   Affiche le nom de la référence.

- **Jeton de clé publique**

   Affiche le jeton de clé publique utilisé pour identifier l'assembly référencé.

- **Nom fort**

   **`true`** Si l’assembly référencé a un nom fort. Un assembly à nom fort est associé à une version unique.

- **Version**

   Affiche la version de l'assembly référencé.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les pages de propriétés de projet C++](reference/property-pages-visual-cpp.md)<br>
[Définir le compilateur C++ et les propriétés de build dans Visual Studio](working-with-project-properties.md)
