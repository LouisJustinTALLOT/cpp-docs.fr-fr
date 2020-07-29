---
title: 'Procédure : Migrer vers -clr'
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
ms.openlocfilehash: 0c21fe585049ebce6383c5d8f673704e7362cd72
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225694"
---
# <a name="how-to-migrate-to-clr"></a>Comment : effectuer une migration vers /clr

Cette rubrique décrit les problèmes qui surviennent lors de la compilation de code natif avec **/CLR** (pour plus d’informations, consultez [/clr (compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) . **/CLR** permet au code c++ natif d’appeler et d’être appelé à partir d’assemblys .net en plus d’un autre code c++ natif. Pour plus d’informations sur les avantages de la compilation avec **/CLR**, consultez [assemblys mixtes (natifs et managés)](../dotnet/mixed-native-and-managed-assemblies.md) et [interopérabilité native et .net](../dotnet/native-and-dotnet-interoperability.md) .

## <a name="known-issues-compiling-library-projects-with-clr"></a>Problèmes connus de compilation de projets de bibliothèque avec/CLR

Visual Studio contient des problèmes connus lors de la compilation de projets de bibliothèque avec **/CLR**:

- Votre code peut interroger des types au moment de l’exécution avec [CRuntimeClass :: FromName](../mfc/reference/cruntimeclass-structure.md#fromname). Toutefois, si un type se trouve dans un fichier MSIL. dll (compilé avec **/CLR**), l’appel à `FromName` peut échouer s’il se produit avant l’exécution des constructeurs statiques dans le fichier. dll managé (vous ne verrez pas ce problème si l’appel FromName se produit après l’exécution du code dans le fichier. dll managé). Pour contourner ce problème, vous pouvez forcer la construction du constructeur statique géré en définissant une fonction dans le fichier. dll managé, en l’exportant et en l’appelant à partir de l’application MFC native. Par exemple :

    ```
    // MFC extension DLL Header file:
    __declspec( dllexport ) void EnsureManagedInitialization () {
       // managed code that won't be optimized away
       System::GC::KeepAlive(System::Int32::MaxValue);
    }
    ```

## <a name="compile-with-visual-c"></a>Compiler avec Visual C++

Avant d’utiliser **/CLR** sur un module de votre projet, compilez et liez d’abord votre projet natif à Visual Studio 2010.

Les étapes suivantes, suivies dans l’ordre, fournissent le chemin d’accès le plus simple à une compilation **/CLR** . Il est important de compiler et d’exécuter votre projet après chacune de ces étapes.

### <a name="versions-prior-to-visual-studio-2003"></a>Versions antérieures à Visual Studio 2003

Si vous effectuez une mise à niveau vers Visual Studio 2010 à partir d’une version antérieure à Visual Studio 2003, vous pouvez voir des erreurs de compilateur liées à la conformité à la norme C++ améliorée dans Visual Studio 2003

### <a name="upgrading-from-visual-studio-2003"></a>Mise à niveau à partir de Visual Studio 2003

Les projets générés précédemment à l’aide de Visual Studio 2003 doivent également être compilés sans **/CLR** , car Visual Studio a désormais une conformité ANSI/ISO accrue et des modifications avec rupture. La modification qui est susceptible de nécessiter la plus grande attention est celle des [fonctionnalités de sécurité dans le CRT](../c-runtime-library/security-features-in-the-crt.md). Le code qui utilise le CRT est très susceptible de produire des avertissements de désapprobation. Ces avertissements peuvent être supprimés, mais il est préférable de migrer vers les nouvelles [versions à sécurité améliorée des fonctions CRT](../c-runtime-library/security-enhanced-versions-of-crt-functions.md) , car elles fournissent une meilleure sécurité et peuvent révéler des problèmes de sécurité dans votre code.

### <a name="upgrading-from-managed-extensions-for-c"></a>Mise à niveau à partir de Extensions managées pour C++

À compter de Visual Studio 2005, le code écrit avec Extensions managées pour C++ ne sera pas compilé sous **/CLR**.

## <a name="convert-c-code-to-c"></a>Convertir du code C en C++

Bien que Visual Studio compile des fichiers C, il est nécessaire de les convertir en C++ pour une compilation **/CLR** . Il n’est pas nécessaire de modifier le nom de fichier réel ; vous pouvez utiliser **/TP** (voir [/TC,/TP,/TC,/TP (spécifier le type de fichier source)](../build/reference/tc-tp-tc-tp-specify-source-file-type.md).) Notez que même si les fichiers de code source C++ sont requis pour **/CLR**, il n’est pas nécessaire de refactoriser votre code pour utiliser des paradigmes orientés objet.

Le code C nécessite très probablement des modifications lorsqu’il est compilé en tant que fichier C++. Les règles de sécurité de type C++ étant strictes, les conversions de type doivent être rendues explicites avec les casts. Par exemple, malloc retourne un pointeur void, mais peut être assigné à un pointeur vers n’importe quel type en C avec un cast :

```
int* a = malloc(sizeof(int));   // C code
int* b = (int*)malloc(sizeof(int));   // C++ equivalent
```

Les pointeurs fonction étant également strictement de type sécurisé en C++, le code C suivant nécessite une modification. En C++, il est préférable de créer un **`typedef`** qui définit le type de pointeur de fonction, puis d’utiliser ce type pour caster des pointeurs de fonction :

```
NewFunc1 = GetProcAddress( hLib, "Func1" );   // C code
typedef int(*MYPROC)(int);   // C++ equivalent
NewFunc2 = (MYPROC)GetProcAddress( hLib, "Func2" );
```

C++ exige également que les fonctions soient prototypées ou entièrement définies avant de pouvoir être référencées ou appelées.

Les identificateurs utilisés dans le code C qui sont des mots clés en C++ (tels que,,,,, **`virtual`** **`new`** **`delete`** **`bool`** **`true`** **`false`** , etc.) doivent être renommés. Cela peut généralement être fait avec des opérations de recherche et de remplacement simples.

```
COMObj1->lpVtbl->Method(COMObj, args);  // C code
COMObj2->Method(args);  // C++ equivalent
```

## <a name="reconfigure-project-settings"></a>Reconfigurer les paramètres du projet

Une fois que votre projet est compilé et exécuté dans Visual Studio 2010, vous devez créer de nouvelles configurations de projet pour **/CLR** au lieu de modifier les configurations par défaut. **/CLR** est incompatible avec certaines options du compilateur et la création de configurations distinctes vous permet de générer votre projet en tant que code natif ou managé. Quand **/CLR** est sélectionné dans la boîte de dialogue pages de propriétés, les paramètres de projet non compatibles avec **/CLR** sont désactivés (et les options désactivées ne sont pas restaurées automatiquement si **/CLR** est désélectionné par la suite).

### <a name="create-new-project-configurations"></a>Créer des configurations de projet

Vous pouvez utiliser l’option **copier les paramètres de** dans la **boîte de dialogue nouvelle configuration de projet** (**générer**  >  **Configuration Manager**  >  **configuration de solution active**  >  **nouveau**) pour créer une configuration de projet basée sur vos paramètres de projet existants. Effectuez cette opération une fois pour la configuration Debug et une fois pour la configuration Release. Les modifications ultérieures peuvent ensuite être appliquées uniquement aux configurations spécifiques à **/CLR** , en laissant intactes les configurations de projet d’origine.

Les projets qui utilisent des règles de génération personnalisées peuvent nécessiter une attention particulière.

Cette étape a des implications différentes pour les projets qui utilisent des makefiles. Dans ce cas, une cible de génération distincte peut être configurée, ou une version spécifique à la compilation **/CLR** peut être créée à partir d’une copie de l’original.

### <a name="change-project-settings"></a>Modifier les paramètres du projet

vous pouvez sélectionner **/CLR** dans l’environnement de développement en suivant les instructions fournies dans [/clr (compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md). Comme mentionné précédemment, cette étape désactive automatiquement les paramètres de projet en conflit.

> [!NOTE]
> Lors de la mise à niveau d’une bibliothèque managée ou d’un projet de service Web à partir de Visual Studio 2003, l’option de compilateur **/zl** sera ajoutée à la page de propriétés **ligne de commande** . Cela provoque l’LNK2001. Supprimez **/zl** de la page de propriétés **ligne de commande** pour résoudre. Pour plus d’informations, consultez [/zl (omettre le nom de la bibliothèque par défaut)](../build/reference/zl-omit-default-library-name.md) et [définir les propriétés du compilateur et](../build/working-with-project-properties.md) de la Build. Ou ajoutez Msvcrt. lib et msvcmrt. lib à la propriété **dépendances supplémentaires** de l’éditeur de liens.

Pour les projets générés avec des makefiles, les options de compilateur incompatibles doivent être désactivées manuellement une fois que **/CLR** est ajouté. Consultez[restrictions//CLR](../build/reference/clr-restrictions.md) pour plus d’informations sur les options du compilateur qui ne sont pas compatibles avec **/CLR**.

### <a name="precompiled-headers"></a>En-têtes précompilés

Les en-têtes précompilés sont pris en charge sous **/CLR**. Toutefois, si vous compilez uniquement certains de vos fichiers CPP avec **/CLR** (en compilant le reste en natif), certaines modifications sont nécessaires, car les en-têtes précompilés générés avec **/CLR** ne sont pas compatibles avec ceux générés sans **/CLR**. Cette incompatibilité est due au fait que **/CLR** génère et nécessite des métadonnées. Modules compilés **/CLR** ne peut donc pas utiliser des en-têtes précompilés qui n’incluent pas de métadonnées, et les modules non- **/CLR** ne peuvent pas utiliser des fichiers d’en-tête précompilés qui contiennent des métadonnées.

Le moyen le plus simple de compiler un projet où certains modules sont compilés **/CLR** est de désactiver entièrement les en-têtes précompilés. (Dans la boîte de dialogue pages de propriétés du projet, ouvrez le nœud C/C++, puis sélectionnez en-têtes précompilés. Modifiez ensuite la propriété créer/utiliser des en-têtes précompilés sur « pas à l’aide des en-têtes précompilés ».)

Toutefois, en particulier pour les grands projets, les en-têtes précompilés offrent une plus grande rapidité de compilation. par conséquent, la désactivation de cette fonctionnalité n’est pas souhaitable. Dans ce cas, il est préférable de configurer les fichiers **/CLR** et non **/CLR** pour utiliser des en-têtes précompilés distincts. Vous pouvez effectuer cette opération en une seule étape en sélectionnant les modules **à compiler à** l’aide de **Explorateur de solutions**, en cliquant avec le bouton droit sur le groupe et en sélectionnant Propriétés. Modifiez ensuite les propriétés créer/utiliser PCH par le fichier et en-tête précompilé pour utiliser respectivement un nom de fichier d’en-tête et un fichier PCH différents.

## <a name="fixing-errors"></a>Correction des erreurs

La compilation avec **/CLR** peut entraîner des erreurs du compilateur, de l’éditeur de liens ou du Runtime. Cette section décrit les problèmes les plus courants.

### <a name="metadata-merge"></a>Fusion des métadonnées

Les différentes versions des types de données peuvent provoquer l’échec de l’éditeur de liens, car les métadonnées générées pour les deux types ne correspondent pas. (Cela est généralement dû au fait que les membres d’un type sont définis de manière conditionnelle, mais que les conditions ne sont pas les mêmes pour tous les fichiers CPP qui utilisent le type.) Dans ce cas, l’éditeur de liens échoue, en signalant uniquement le nom du symbole et le nom du deuxième fichier OBJ où le type a été défini. Il est souvent utile de faire pivoter l’ordre dans lequel les fichiers OBJ sont envoyés à l’éditeur de liens pour découvrir l’emplacement de l’autre version du type de données.

### <a name="loader-lock-deadlock"></a>Verrou mortel du chargeur

Le « blocage du verrou de chargeur » peut se produire, mais il est déterministe et est détecté et signalé au moment de l’exécution. Pour obtenir des informations détaillées, des conseils et des solutions, consultez [initialisation des assemblys mixtes](../dotnet/initialization-of-mixed-assemblies.md) .

### <a name="data-exports"></a>Exportations de données

L’exportation de données de DLL est sujette aux erreurs et n’est pas recommandée. Cela est dû au fait que la section de données d’une DLL n’est pas nécessairement initialisée tant qu’une partie managée de la DLL n’a pas été exécutée. Référencez les métadonnées avec [#using directive](../preprocessor/hash-using-directive-cpp.md).

### <a name="type-visibility"></a>Visibilité du type

Les types natifs sont privés par défaut. Cela peut entraîner un type natif qui n’est pas visible à l’extérieur de la DLL. Résolvez cette erreur en ajoutant **`public`** à ces types.

### <a name="floating-point-and-alignment-issues"></a>Problèmes de virgule flottante et d’alignement

`__controlfp`n’est pas pris en charge sur le common language runtime (consultez [_control87, _controlfp, \_ _control87_2](../c-runtime-library/reference/control87-controlfp-control87-2.md) pour plus d’informations). Le CLR ne respecte pas non plus l' [alignement](../cpp/align-cpp.md).

### <a name="com-initialization"></a>Initialisation COM

Le Common Language Runtime Initialise automatiquement COM lorsqu’un module est initialisé (quand COM est initialisé automatiquement, il est effectué comme MTA). Par conséquent, l’initialisation explicite de COM génère des codes de retour indiquant que COM est déjà initialisé. Toute tentative d’initialisation explicite de COM avec un modèle de thread lorsque le CLR a déjà initialisé COM sur un autre modèle de thread peut entraîner l’échec de votre application.

Le common language runtime démarre COM en tant que MTA par défaut ; Utilisez [/CLRTHREADATTRIBUTE (définir l’attribut de thread CLR)](../build/reference/clrthreadattribute-set-clr-thread-attribute.md) pour modifier cela.

### <a name="performance-issues"></a>Problèmes de performance

Vous pouvez constater une baisse des performances lorsque les méthodes C++ natives générées en langage MSIL sont appelées indirectement (appels de fonction virtuelle ou utilisation de pointeurs de fonction). Pour en savoir plus à ce sujet, consultez [double médiateur](../dotnet/double-thunking-cpp.md).

Lors du passage de Native à MSIL, vous remarquerez une augmentation de la taille de votre plage de travail. Cela est dû au fait que le common language runtime fournit de nombreuses fonctionnalités pour s’assurer que les programmes s’exécutent correctement. Si votre application **/CLR** ne s’exécute pas correctement, vous pouvez activer C4793 (désactivé par défaut). pour plus d’informations, consultez [Avertissement du compilateur (niveaux 1 et 3) C4793](../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md) .

### <a name="program-crashes-on-shutdown"></a>Blocage du programme lors de l’arrêt

Dans certains cas, le CLR peut être arrêté avant la fin de l’exécution de votre code managé. L’utilisation `std::set_terminate` de et `SIGTERM` peut entraîner ce problème. Pour plus d’informations, consultez [constantes de signal](../c-runtime-library/signal-constants.md) et [set_terminate](../c-runtime-library/abnormal-termination.md) .

## <a name="using-new-visual-c-features"></a>Utilisation des nouvelles fonctionnalités de Visual C++

Après compilation, liaison et exécution de votre application, vous pouvez commencer à utiliser les fonctionnalités .NET dans n’importe quel module compilé avec **/CLR**. Pour plus d’informations, consultez [Extensions de composant pour les plateformes Runtime](../extensions/component-extensions-for-runtime-platforms.md).

Pour plus d’informations sur la programmation .NET dans Visual C++ consultez :

- [Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

- [Interopérabilité native et .NET](../dotnet/native-and-dotnet-interoperability.md)

- [Extensions de composant pour les plateformes Runtime](../extensions/component-extensions-for-runtime-platforms.md)

## <a name="see-also"></a>Voir aussi

[Assemblys mixtes (natifs et managés)](../dotnet/mixed-native-and-managed-assemblies.md)
