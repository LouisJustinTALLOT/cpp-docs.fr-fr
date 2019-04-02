---
title: Utilisation des bibliothèques et des composants dans les projets C++
ms.date: 12/10/2018
f1_keywords:
- VC.Project.References
helpviewer_keywords:
- Add References Dialog Box (C++)
- .NET Framework (C++), Add References Dialog Box
ms.assetid: 12b8f571-0f21-40b3-9404-5318a57e9cb5
ms.openlocfilehash: eb4d970527ba919af10eadab7c907f5108767b9b
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58780468"
---
# <a name="consuming-libraries-and-components"></a>Utilisation des bibliothèques et composants

Souvent, un projet C++ doit appeler des fonctions ou accéder aux données dans un fichier binaire comme bibliothèque statique (fichiers .lib), DLL, composant de Windows Runtime, COM ou un assembly .NET. Dans ce cas, vous devez configurer le projet pour qu’il puisse trouver ce code binaire au moment de la génération. Les étapes spécifiques varient selon le type de votre projet, le type du fichier binaire, et indique si le fichier binaire est généré dans la même solution que votre projet. 

## <a name="consuming-libraries-downloaded-via-vcpkg"></a>Utilisation des bibliothèques téléchargés via vcpkg

Pour utiliser une bibliothèque que vous avez téléchargé à l’aide de la **vcpkg** Gestionnaire de package, vous pouvez ignorer les instructions ci-dessous. Consultez [vcpkg : Gestionnaire de package C++ pour Windows, Linux et MacOS](vcpkg.md#integrate-with-visual-studio-windows) pour plus d’informations.

## <a name="consuming-static-libraries"></a>Utilisation des bibliothèques statiques

Si votre projet de bibliothèque statique est généré dans la même solution :

1. #<a name="include-the-header-files-for-the-static-library-using-quotation-marks-in-a-typical-solution-the-path-will-start-with-library-project-name-intellisense-will-help-you-find-it"></a>inclure les fichiers d’en-tête pour la bibliothèque statique à l’aide de guillemets. Dans une solution classique commence par le chemin d’accès `../<library project name>`. IntelliSense vous aidera à trouver.
2. Ajoutez une référence au projet de bibliothèque statique. Avec le bouton droit sur **références** sous le nœud de projet d’application dans **l’Explorateur de solutions** et choisissez **ajouter une référence**. 

Si la bibliothèque statique ne fait pas partie de la solution :

1. Avec le bouton droit sur le nœud de projet d’application dans **l’Explorateur de solutions** , puis **propriétés**. 
2. Dans le **répertoires VC ++** propriété page, ajoutez le chemin d’accès au répertoire où se trouve le fichier .lib dans **chemins d’accès de la bibliothèque** et ajoutez le chemin d’accès aux fichiers d’en-tête de bibliothèque dans **répertoires Include** .  
3. Dans le **l’éditeur de liens > entrée** propriété page, ajoutez le nom du fichier .lib à **dépendances supplémentaires**.

## <a name="dynamic-link-libraries"></a>Bibliothèques de liens dynamiques

Si la DLL est générée dans le cadre de la même solution que l’application, suivez les mêmes étapes que pour une bibliothèque statique.

Si la DLL ne fait pas partie de la solution d’application, vous devez le fichier DLL, les en-têtes avec des prototypes pour les classes et les fonctions exportées et un fichier .lib qui fournit les informations de liaison nécessaires.

1. Copiez la DLL dans le dossier de sortie de votre projet, ou vers un autre dossier dans le chemin de recherche Windows standard pour les DLL. Consultez [Dynamic-Link Library Search Order](/windows/desktop/dlls/dynamic-link-library-search-order).
2. Suivez les étapes 1 à 3 pour les bibliothèques statiques fournir les chemins d’accès pour les en-têtes et le fichier .lib.

## <a name="com-objects"></a>objets COM

Si votre application C++ native doit utiliser un objet COM, et cet objet est *inscrit*, il vous est alors appelez CoCreateInstance et passez le CLSID de l’objet. Le système le trouver dans le Registre Windows et le charger. C++ / c++ / projet CLI peut consommer un objet COM de la même façon, ou en ajoutant une référence à celui-ci à partir de la **ajouter des références > COM** liste et le consommer via son [wrapper RCW](/dotnet/framework/interop/runtime-callable-wrapper). 

## <a name="net-assemblies-and-windows-runtime-components"></a>Assemblys .NET et composants Windows Runtime

Dans UWP ou C++ / c++ / projets de l’interface CLI, vous consommez des assemblys .NET ou composants Windows Runtime en ajoutant un *référence* à l’assembly ou le composant. Sous le **références** nœud dans un UWP ou C++ / c++ / CLI project, vous voyez des références aux composants couramment utilisés. Avec le bouton droit sur le **références** nœud dans **l’Explorateur de solutions** pour faire apparaître le **Gestionnaire de références** et parcourir des composants supplémentaires qui sont connus pour le système. Cliquez sur le **Parcourir** bouton pour accéder à n’importe quel dossier où se trouve un composant personnalisé. Étant donné que les assemblys .NET et les composants Windows Runtime contiennent des informations de type intégré, vous pouvez afficher leurs classes et méthodes en effectuant un clic droit et en choisissant **afficher dans le navigateur de l’objet**. 

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

### <a name="assembly-reference-properties-ccli"></a>Propriétés de référence d’assembly (C++ / c++ / CLI)

Propriétés de référence d’assembly sont disponibles uniquement pour les références aux assemblys .NET Framework en C / c++ / projets de l’interface CLI. Ces propriétés sont affichées uniquement lorsqu’un assembly .NET Framework est sélectionné dans le **références** volet. Les propriétés ne peuvent pas être modifiées.

- **Chemin d’accès relatif**

   Affiche le chemin d'accès relatif du répertoire de projet à l'assembly référencé.

### <a name="build-properties"></a>Propriétés de build

Les propriétés suivantes sont disponibles sur divers genres de références. Elles vous permettent de spécifier le mode de génération avec des références.

- **Copie locale**

   Spécifie si l'assembly référencé doit être copié automatiquement vers l'emplacement cible pendant une génération.

- **Copiez les assemblys satellites locaux (C++ / c++ / CLI)**

   Spécifie si les assemblys satellites de l'assembly référencé doivent être copiés automatiquement vers l'emplacement cible pendant une génération. Utilisé uniquement si **Copie locale** a la valeur **true**.

- **Sortie de l’assembly de référence**

   Spécifie que cet assembly est utilisé dans le processus de génération. Si la valeur est **true**, l'assembly est utilisé sur la ligne de commande du compilateur durant la génération.

### <a name="project-to-project-reference-properties"></a>Propriétés de référence entre projets

Les propriétés suivantes définissent un *référence de projet à projet* à partir du projet est sélectionné dans le **références** volet à un autre projet dans la même solution. Pour plus d’informations, consultez [Gestion des références dans un projet](/visualstudio/ide/managing-references-in-a-project).

- **Lier les dépendances de la bibliothèque**

   Quand cette propriété a la valeur **True**, le système de projet lie au projet dépendant les fichiers .lib produits par le projet indépendant. En général, vous devez spécifier **True**.

- **Identificateur de projet**

   Identifie de façon unique le projet indépendant. La valeur de propriété est un GUID système interne qui ne peut pas être modifié.

- **Utiliser les entrées de dépendance de la bibliothèque**

   Quand cette propriété a la valeur **False**, le système de projet ne lie pas au projet dépendant les fichiers .obj de la bibliothèque produite par le projet indépendant. Ainsi, cette valeur désactive la liaison incrémentielle. En général, vous spécifiez **False** , car la génération de l'application peut prendre du temps, s'il existe de nombreux projets indépendants.

### <a name="read-only-reference-properties-com--net"></a>Propriétés de la référence en lecture seule (COM et .NET)

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

[Référence de page de propriété de projet C++](reference/property-pages-visual-cpp.md)<br>
[Définir le compilateur C++ et les propriétés de build dans Visual Studio](working-with-project-properties.md)