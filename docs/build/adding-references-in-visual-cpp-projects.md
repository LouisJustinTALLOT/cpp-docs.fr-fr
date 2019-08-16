---
title: Utilisation de bibliothèques et de composants C++ dans des projets
ms.date: 12/10/2018
f1_keywords:
- VC.Project.References
helpviewer_keywords:
- Add References Dialog Box (C++)
- .NET Framework (C++), Add References Dialog Box
ms.assetid: 12b8f571-0f21-40b3-9404-5318a57e9cb5
ms.openlocfilehash: a65ad69914b14e7b8b37c321fa7d06740af57e3a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493384"
---
# <a name="consuming-libraries-and-components"></a>Utilisation de bibliothèques et de composants

Souvent, un C++ projet doit appeler des fonctions ou accéder aux données dans un fichier binaire, tel qu’une bibliothèque statique (fichiers. lib), une dll, un composant Windows Runtime, un composant com ou un assembly .net. Dans ce cas, vous devez configurer le projet afin qu’il puisse trouver ce fichier binaire au moment de la génération. Les étapes spécifiques dépendent du type de votre projet, du type de fichier binaire et de l’éventuelle génération du fichier binaire dans la même solution que votre projet. 

## <a name="consuming-libraries-downloaded-via-vcpkg"></a>Utilisation de bibliothèques téléchargées via vcpkg

Pour utiliser une bibliothèque que vous avez téléchargée à l’aide du gestionnaire de package **vcpkg** , vous pouvez ignorer les instructions ci-dessous. Consultez [vcpkg : Un C++ gestionnaire de package pour Windows, Linux et](vcpkg.md#integrate-with-visual-studio-windows) MacOS pour plus d’informations.

## <a name="consuming-static-libraries"></a>Utilisation de bibliothèques statiques

Si votre projet de bibliothèque statique est généré dans la même solution:

1. #<a name="include-the-header-files-for-the-static-library-using-quotation-marks-in-a-typical-solution-the-path-will-start-with-library-project-name-intellisense-will-help-you-find-it"></a>incluez le ou les fichiers d’en-tête pour la bibliothèque statique à l’aide de guillemets. Dans une solution standard, le chemin d’accès `../<library project name>`commence par. IntelliSense vous aide à le trouver.
2. Ajoutez une référence au projet de bibliothèque statique. Cliquez avec le bouton droit sur **références** sous le nœud projet d’application dans **Explorateur de solutions** et choisissez **Ajouter une référence**. 

Si la bibliothèque statique ne fait pas partie de la solution:

1. Dans **Explorateur de solutions** , cliquez avec le bouton droit sur le nœud du projet d’application, puis choisissez **Propriétés**. 
2. Dans la page de propriétés **Répertoires VC + +** , ajoutez le chemin d’accès au répertoire où se trouve le fichier. lib dans les **chemins d’accès de bibliothèque** , puis ajoutez le chemin d’accès au (x) fichier (s) d’en-tête de bibliothèque dans les répertoires **include**.  
3. Dans l' **éditeur de liens >** page de propriétés d’entrée, ajoutez le nom du fichier. lib aux **dépendances supplémentaires**.

## <a name="dynamic-link-libraries"></a>Bibliothèques de liens dynamiques

Si la DLL est générée dans le cadre de la même solution que l’application, suivez les mêmes étapes que pour une bibliothèque statique.

Si la DLL ne fait pas partie de la solution d’application, vous avez besoin du fichier DLL, des en-têtes avec des prototypes pour les fonctions et les classes exportées, et d’un fichier. lib qui fournit les informations de liaison nécessaires.

1. Copiez la DLL dans le dossier de sortie de votre projet ou dans un autre dossier du chemin d’accès de recherche Windows standard pour les dll. Consultez l' [ordre de recherche de la bibliothèque de liens dynamiques](/windows/win32/dlls/dynamic-link-library-search-order).
2. Suivez les étapes 1-3 pour les bibliothèques statiques pour fournir les chemins d’accès aux en-têtes et au fichier. lib.

## <a name="com-objects"></a>objets COM

Si votre application C++ Native doit consommer un objet com et que cet objet est *inscrit*, il vous suffit d’appeler CoCreateInstance et de transmettre le CLSID de l’objet. Le système le trouvera dans le Registre Windows et le chargera. Un C++projet/CLI peut utiliser un objet com de la même manière, ou en ajoutant une référence à partir de la liste **ajouter des références > com** et en l’utilisant via son [Wrapper pouvant être appelé](/dotnet/framework/interop/runtime-callable-wrapper)par le Runtime. 

## <a name="net-assemblies-and-windows-runtime-components"></a>Assemblys .NET et composants de Windows Runtime

Dans les projets C++UWP ou/CLI, vous consommez des assemblys .net ou des composants Windows Runtime en ajoutant une *référence* à l’assembly ou au composant. Sous le nœud **références** dans un projet UWP C++ou/CLI, vous pouvez voir des références à des composants couramment utilisés. Cliquez avec le bouton droit sur le nœud **références** dans **Explorateur de solutions** pour afficher le **Gestionnaire de références** et parcourir les autres composants connus du système. Cliquez sur le bouton **Parcourir** pour accéder à un dossier où se trouve un composant personnalisé. Étant donné que les assemblys .NET et les composants Windows Runtime contiennent des informations de type intégrées, vous pouvez afficher leurs méthodes et classes en cliquant avec le bouton droit et en sélectionnant **afficher dans l’Explorateur d’objets**. 

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

### <a name="assembly-reference-properties-ccli"></a>Propriétés de référence deC++l’assembly (/CLI)

Les propriétés de référence d’assembly sont disponibles uniquement pour les C++références aux assemblys .NET Framework dans les projets/CLI. Ces propriétés s’affichent uniquement lorsqu’un assembly de .NET Framework est sélectionné dans le volet **références** . Les propriétés ne peuvent pas être modifiées.

- **Chemin d’accès relatif**

   Affiche le chemin d'accès relatif du répertoire de projet à l'assembly référencé.

### <a name="build-properties"></a>Propriétés de build

Les propriétés suivantes sont disponibles sur divers genres de références. Elles vous permettent de spécifier le mode de génération avec des références.

- **Copie locale**

   Spécifie si l'assembly référencé doit être copié automatiquement vers l'emplacement cible pendant une génération.

- **Copier les assemblys satellites locauxC++(/CLI)**

   Spécifie si les assemblys satellites de l'assembly référencé doivent être copiés automatiquement vers l'emplacement cible pendant une génération. Utilisé uniquement si **Copie locale** a la valeur **true**.

- **Sortie de l’assembly de référence**

   Spécifie que cet assembly est utilisé dans le processus de génération. Si la valeur est **true**, l'assembly est utilisé sur la ligne de commande du compilateur durant la génération.

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

- **Nom de l'assembly**

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

- **Name**

   Affiche le nom de la référence.

- **Jeton de clé publique**

   Affiche le jeton de clé publique utilisé pour identifier l'assembly référencé.

- **Nom fort**

   `true` si l'assembly référencé a un nom fort. Un assembly à nom fort est associé à une version unique.

- **Version**

   Affiche la version de l'assembly référencé.

## <a name="see-also"></a>Voir aussi

[C++Référence de la page de propriétés du projet](reference/property-pages-visual-cpp.md)<br>
[Définir le compilateur C++ et les propriétés de build dans Visual Studio](working-with-project-properties.md)