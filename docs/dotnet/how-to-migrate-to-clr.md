---
title: 'Procédure : Migration vers / clr'
ms.custom: get-started-article
ms.date: 09/18/2018
helpviewer_keywords:
- upgrading Visual C++ applications, /clr compiler option
- compiling native code [C++]
- interoperability [C++], /clr compiler option
- interop [C++], /clr compiler option
- migration [C++], /clr compiler option
- /clr compiler option [C++], porting to
ms.assetid: c9290b8b-436a-4510-8b56-eae51f4a9afc
ms.openlocfilehash: 8c4827891799d2c76a344e4c6da8f3d96333826e
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816030"
---
# <a name="how-to-migrate-to-clr"></a>Procédure : Migrer vers/CLR

Cette rubrique traite des problèmes qui surviennent lors de la compilation de code natif avec **/CLR** (consultez [/clr (Compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) pour plus d’informations). **/ CLR** permet à du code C++ natif à appeler et d’être appelés à partir des assemblys .NET en plus de tout autre code C++ natif. Consultez [assemblys mixtes (natif et managé)](../dotnet/mixed-native-and-managed-assemblies.md) et [natif et l’interopérabilité .NET](../dotnet/native-and-dotnet-interoperability.md) pour plus d’informations sur les avantages de la compilation avec **/CLR**.

## <a name="known-issues-compiling-library-projects-with-clr"></a>Connus problèmes de compilation de projets de bibliothèque avec/CLR

Visual Studio contient des problèmes connus lors de la compilation des projets de bibliothèque avec **/CLR**:

- Votre code peut interroger des types lors de l’exécution avec [CRuntimeClass::FromName](../mfc/reference/cruntimeclass-structure.md#fromname). Toutefois, si un type est dans un fichier .dll MSIL (compilé avec **/CLR**), l’appel à `FromName` peut échouer si elle se produit avant que les constructeurs statiques exécutées dans le .dll managé (vous ne verrez pas ce problème si l’appel FromName se produit une fois que le code a exécutée dans le .dll managé). Pour contourner ce problème, vous pouvez forcer la construction du constructeur statique managé en définissant une fonction dans le .dll managé, son exportation et appeler à partir de l’application MFC native. Exemple :

    ```
    // MFC extension DLL Header file:
    __declspec( dllexport ) void EnsureManagedInitialization () {
       // managed code that won't be optimized away
       System::GC::KeepAlive(System::Int32::MaxValue);
    }
    ```

## <a name="compile-with-visual-c"></a>Compilez avec Visual C++

Avant d’utiliser **/CLR** sur n’importe quel module dans votre projet, tout d’abord compiler et lier votre projet natif avec Visual Studio 2010.

Les étapes suivantes, suivies dans l’ordre, indiquent le chemin le plus simple pour un **/CLR** compilation. Il est important de compiler et exécuter votre projet après chacune de ces étapes.

### <a name="versions-prior-to-visual-c-2003"></a>Versions antérieures à Visual C++ 2003

Si vous mettez à niveau vers Visual Studio 2010 à partir d’une version antérieure à Visual C++ 2003, vous pouvez voir des erreurs de compilation liées à la meilleure conformité standard C++ dans Visual C++ 2003

### <a name="upgrading-from-visual-c-2003"></a>La mise à niveau à partir de Visual C++ 2003

Projets antérieurs générés avec Visual C++ 2003 doivent également être compilés d’abord sans **/CLR** comme Visual Studio bénéficie d’une meilleure conformité aux normes ANSI/ISO et des modifications avec rupture. La modification sans doute le plus d’attention est [des fonctionnalités de sécurité dans le CRT](../c-runtime-library/security-features-in-the-crt.md). Code qui utilise la bibliothèque CRT est très probable produire des avertissements de désapprobation. Ces avertissements peuvent être supprimés, mais la migration vers le nouveau [Versions de fonctions CRT](../c-runtime-library/security-enhanced-versions-of-crt-functions.md) est recommandée, car ils fournissent une meilleure sécurité et peuvent révéler des problèmes de sécurité dans votre code.

### <a name="upgrading-from-managed-extensions-for-c"></a>La mise à niveau à partir des Extensions managées pour C++

À partir de Visual Studio 2005, le code écrit avec des Extensions managées pour C++ n’est pas compilé sous **/CLR**.

## <a name="convert-c-code-to-c"></a>Convertir le Code C en C++

Bien que Visual Studio compile les fichiers C, il est nécessaire de les convertir en C++ pour un **/CLR** compilation. Nom de fichier ne doit pas être modifié ; Vous pouvez utiliser **/Tp** (consultez [TP, / TP, /TP (spécifier le Type des fichiers Source)](../build/reference/tc-tp-tc-tp-specify-source-file-type.md).) Notez que bien que les fichiers de code source C++ sont requis pour **/CLR**, il n’est pas nécessaire de refactoriser votre code pour utiliser des paradigmes orientés objet.

Code C est très susceptible de nécessiter des modifications lors de la compilation dans un fichier C++. Les règles de sécurité de type C++ sont stricts, les conversions de type doivent être rendue explicites avec des casts. Par exemple, malloc retourne un pointeur void, mais peut être affecté à un pointeur vers n’importe quel type en C avec un cast :

```
int* a = malloc(sizeof(int));   // C code
int* b = (int*)malloc(sizeof(int));   // C++ equivalent
```

Pointeurs de fonction étant également strictement de type sécurisé en C++, le code C suivant requiert une modification. En C++, il est préférable de créer un `typedef` qui définit le type de pointeur de fonction et ensuite utiliser ce type pour convertir des pointeurs de fonction :

```
NewFunc1 = GetProcAddress( hLib, "Func1" );   // C code
typedef int(*MYPROC)(int);   // C++ equivalent
NewFunc2 = (MYPROC)GetProcAddress( hLib, "Func2" );
```

C++ requiert également être soit prototypée soit entièrement définie avant de pouvoir être référencés ou appelés.

Les identificateurs utilisés dans le code C et qui peuvent être des mots clés en C++ (tels que **virtuels**, **nouveau**, **supprimer**, **bool**, **true** , **false**, etc.) doit être renommé. Généralement procéder avec de simples opérations de recherche et remplacement.

```
COMObj1->lpVtbl->Method(COMObj, args);  // C code
COMObj2->Method(args);  // C++ equivalent
```

## <a name="reconfigure-project-settings"></a>Reconfigurer les paramètres du projet

Une fois que votre projet se compile et s’exécute dans Visual Studio 2010, vous devez créer des configurations de projet pour **/CLR** plutôt que de modifier les configurations par défaut. **/ CLR** est incompatible avec certaines options du compilateur et de la création de configurations séparées vous permet de générer votre projet comme natif ou managé. Lorsque **/CLR** est sélectionné dans la boîte de dialogue des pages de propriété, paramètres du projet non compatibles avec **/CLR** sont désactivés (et les options désactivées ne sont pas restaurées automatiquement si   **/CLR** est désélectionné par la suite).

### <a name="create-new-project-configurations"></a>Créer des Configurations de projet

Vous pouvez utiliser **copier les paramètres de** option dans le **nouvelle boîte de dialogue de Configuration de projet** (**Build** > **deConfigurationManager**  >  **Configuration de la Solution active** > **New**) pour créer une configuration de projet en fonction de vos paramètres de projet existants. Pour cela qu’une seule fois pour la configuration Debug et une fois pour la configuration Release. Les modifications ultérieures apportées peuvent ensuite être appliquées à la **/CLR** -des configurations spécifiques uniquement, laissant les configurations de projet d’origine intact.

Les projets qui utilisent des règles de génération personnalisée peuvent nécessiter une attention supplémentaire.

Cette étape a différentes implications pour les projets qui utilisent des makefiles. Dans ce cas une cible de génération distincte peut être configurée, ou une version spécifique à **/CLR** compilation peut être créée à partir d’une copie de l’original.

### <a name="change-project-settings"></a>Modifier les paramètres de projet

**/ CLR** peuvent être sélectionnés dans l’environnement de développement en suivant les instructions dans [/clr (Compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md). Comme mentionné précédemment, cette étape désactive automatiquement les paramètres de projet en conflit.

> [!NOTE]
>  Mise à niveau d’une bibliothèque managée ou un projet de service web de Visual C++ 2003, le **/Zl** est d’option du compilateur ajoutée dans le **ligne de commande** page de propriétés. Cela entraîne l’erreur LNK2001. Supprimer **/Zl** à partir de la **ligne de commande** page de propriétés. Consultez [/Zl (Omit Default Library Name)](../build/reference/zl-omit-default-library-name.md) et [définir du compilateur et les propriétés de build](../build/working-with-project-properties.md) pour plus d’informations. Ou ajoutez msvcrt.lib et msvcmrt.lib à l’éditeur de liens **dépendances supplémentaires** propriété.

Pour les projets générés avec des makefiles, les options du compilateur incompatible doivent être désactivées manuellement une fois **/CLR** est ajouté. Consultez /[/clr Restrictions](../build/reference/clr-restrictions.md) pour plus d’informations sur les options du compilateur qui ne sont pas compatibles avec **/CLR**.

### <a name="precompiled-headers"></a>En-têtes précompilés

En-têtes précompilés sont pris en charge sous **/CLR**. Toutefois, si vous ne compilez que certains de vos fichiers CPP avec **/CLR** (en compilant le reste en natif) certaines modifications soient nécessaires, car les en-têtes précompilés générés avec **/CLR** ne sont pas compatibles avec ceux généré sans **/CLR**. Cette incompatibilité est due au fait que **/CLR** génère et requiert des métadonnées. Modules compilés **/CLR** peuvent donc pas utiliser des en-têtes précompilés qui n’incluent pas les métadonnées et non **/CLR** modules ne peuvent pas utiliser les fichiers d’en-tête précompilé qui contiennent des métadonnées.

Le moyen le plus simple de compiler un projet dont certains modules sont compilés **/CLR** consiste à désactiver complètement les en-têtes précompilés. (Dans la boîte de dialogue Pages de propriétés de projet, ouvrez le nœud C/C++ et sélectionnez les en-têtes précompilés. Puis remplacez la propriété créer/utiliser des en-têtes précompilés « Pas utiliser les en-têtes précompilés ».)

Toutefois, en particulier pour les grands projets, en-têtes précompilés fournissent bien meilleure vitesse de compilation, afin de désactiver cette fonctionnalité n’est pas souhaitable. Dans ce cas, il est préférable de configurer le **/CLR** et non **/CLR** fichiers à utiliser séparément les en-têtes précompilés. Cela est possible en une seule étape en sélectionnant simultanément les modules à compiler **/CLR** à l’aide de **l’Explorateur de solutions**, clic droit sur le groupe et sélectionnez Propriétés. Puis modifier les propriétés de la création/utilisation PCH via fichier et le fichier d’en-tête précompilé pour utiliser respectivement un nom de fichier d’en-tête différent et un fichier PCH.

## <a name="fixing-errors"></a>Correction des erreurs

Compilation avec **/CLR** peut entraîner des erreurs du compilateur, éditeur de liens ou runtime. Cette section traite des problèmes les plus courants.

### <a name="metadata-merge"></a>Fusion des métadonnées

Différentes versions de types de données peuvent entraîner d’échouer car les métadonnées générées pour les deux types ne correspond pas à l’éditeur de liens. (Cela est généralement dû membres d’un type sont définis de façon conditionnelle, mais les conditions ne sont pas les mêmes pour tous les fichiers CPP qui utilisent le type.) Dans ce cas l’éditeur de liens échoue uniquement le nom du symbole et le nom du deuxième fichier OBJ où le type a été défini. Il est souvent utile faire pivoter l’ordre que les fichiers OBJ sont envoyés à l’éditeur de liens pour découvrir l’emplacement de l’autre version du type de données.

### <a name="loader-lock-deadlock"></a>Blocage du verrou du chargeur

Le « blocage du verrou du chargeur » peut se produire, mais est déterministe et est détecté et signalé lors de l’exécution. Consultez [l’initialisation des assemblys mixtes](../dotnet/initialization-of-mixed-assemblies.md) pour des informations détaillées, des conseils et des solutions.

### <a name="data-exports"></a>Exportations de données

Exportation de données de la DLL est sujette aux erreurs et pas recommandé. Il s’agit, car la section de données d’une DLL n’est pas garantie pour être initialisée avant qu’une partie managée de la DLL a été exécutée. Les métadonnées de référence avec [#using, Directive](../preprocessor/hash-using-directive-cpp.md).

### <a name="type-visibility"></a>Visibilité du type

Les types natifs sont privés par défaut. Cela peut entraîner un type natif ne sont pas visibles en dehors de la DLL. Résoudre cette erreur en ajoutant `public` à ces types.

### <a name="floating-point-and-alignment-issues"></a>Virgule flottante et problèmes d’alignement

`__controlfp` n’est pas pris en charge sur le common language runtime (consultez [_control87, _controlfp, \__control87_2](../c-runtime-library/reference/control87-controlfp-control87-2.md) pour plus d’informations). Le CLR ne respectera pas non plus [aligner](../cpp/align-cpp.md).

### <a name="com-initialization"></a>Initialisation de COM

Le Common Language Runtime initialise automatiquement COM lorsqu’un module est initialisé (lorsque COM est initialisé automatiquement qu’il a exécuté en tant que MTA). Par conséquent, l’initialiser COM explicitement génère les codes de retour indiquant que COM est déjà initialisé. Tente d’initialiser explicitement COM avec un modèle de thread lorsque le CLR a déjà initialisé COM à un autre modèle de thread peut provoquer l’échec de votre application.

Le common language runtime démarre COM en tant que MTA par défaut ; Utilisez [/CLRTHREADATTRIBUTE (définir l’attribut de Thread CLR)](../build/reference/clrthreadattribute-set-clr-thread-attribute.md) pour modifier cela.

### <a name="performance-issues"></a>Problèmes de performances

Vous pouvez voir une diminution des performances lorsque les méthodes C++ natives générées en MSIL sont appelées indirectement (appels de fonction virtuelle ou à l’aide de pointeurs de fonction). Pour plus d’informations, consultez [Double médiateur](../dotnet/double-thunking-cpp.md).

Lors du déplacement du code natif en langage MSIL, vous remarquerez une augmentation de la taille de votre jeu de travail. Il s’agit, car le common language runtime fournit de nombreuses fonctionnalités pour vous assurer que les programmes s’exécutent correctement. Si votre **/CLR** application ne fonctionne pas correctement, vous pouvez activer C4793 (désactivé par défaut), consultez [Avertissement du compilateur (niveau 1 et 3) C4793](../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md) pour plus d’informations.

### <a name="program-crashes-on-shutdown"></a>Incidents de programme lors de l’arrêt

Dans certains cas, le CLR puisse s’arrêter avant la fin de votre code managé en cours d’exécution. À l’aide de `std::set_terminate` et `SIGTERM` peuvent entraîner ce problème. Consultez [signal, constantes](../c-runtime-library/signal-constants.md) et [set_terminate](../c-runtime-library/abnormal-termination.md) pour plus d’informations.

## <a name="using-new-visual-c-features"></a>À l’aide des nouvelles fonctionnalités de Visual C++

Une fois votre application compilée, liens et s’exécute, commencer à utiliser des fonctionnalités .NET dans n’importe quel module compilé avec **/CLR**. Pour plus d’informations, consultez [Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md).

Si vous avez utilisé des Extensions managées pour C++, vous pouvez convertir votre code pour utiliser la nouvelle syntaxe. Pour plus d’informations sur la conversion d’Extensions managées pour C++, consultez [C++ / c++ / CLI Migration Primer](../dotnet/cpp-cli-migration-primer.md).

Pour plus d’informations sur la programmation dans Visual C++ .NET, consultez :

- [Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

- [Interopérabilité native et .NET](../dotnet/native-and-dotnet-interoperability.md)

- [Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)

## <a name="see-also"></a>Voir aussi

[Assemblys mixtes (natif et managé)](../dotnet/mixed-native-and-managed-assemblies.md)
