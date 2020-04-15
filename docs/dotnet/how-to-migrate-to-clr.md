---
title: Guide pratique pour effectuer une migration vers -clr
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
ms.openlocfilehash: 339b1f3172d8b82ece3e98f117f53ed399cbd4e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376081"
---
# <a name="how-to-migrate-to-clr"></a>Comment : effectuer une migration vers /clr

Ce sujet traite des questions qui se posent lors de la compilation du code natif avec **/clr** (voir [/clr (Common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md) pour plus d’informations). **/clr** permet au code CMD natif d’invoquer et d’être invoqué à partir d’assemblages .NET en plus d’autres codes CMD indigènes. Voir [Mixed (Native and Managed) Assemblies](../dotnet/mixed-native-and-managed-assemblies.md) and [Native and .NET Interopérabilité](../dotnet/native-and-dotnet-interoperability.md) pour plus d’informations sur les avantages de la compilation avec **/clr**.

## <a name="known-issues-compiling-library-projects-with-clr"></a>Questions connues Compilant des projets de bibliothèque avec /clr

Visual Studio contient quelques problèmes connus lors de la compilation de projets de bibliothèque avec **/clr:**

- Votre code peut interroger les types à l’heure d’exécution avec [CRuntimeClass:FromName](../mfc/reference/cruntimeclass-structure.md#fromname). Toutefois, si un type est dans un MSIL .dll (compilé avec **/clr),** l’appel à `FromName` peut échouer si elle se produit avant que les constructeurs statiques exécutés dans le .dll géré (vous ne verrez pas ce problème si l’appel FromName se produit après le code a exécuté dans le .dll géré). Pour contourner ce problème, vous pouvez forcer la construction du constructeur statique géré en définissant une fonction dans le .dll géré, l’exporter, et l’invoquer à partir de l’application native MFC. Par exemple :

    ```
    // MFC extension DLL Header file:
    __declspec( dllexport ) void EnsureManagedInitialization () {
       // managed code that won't be optimized away
       System::GC::KeepAlive(System::Int32::MaxValue);
    }
    ```

## <a name="compile-with-visual-c"></a>Compiler avec Visual C

Avant d’utiliser **/clr** sur n’importe quel module de votre projet, compilez d’abord et liez votre projet natif avec Visual Studio 2010.

Les étapes suivantes, suivies dans l’ordre, offrent le chemin le plus facile à une compilation **/clr.** Il est important de compiler et d’exécuter votre projet après chacune de ces étapes.

### <a name="versions-prior-to-visual-studio-2003"></a>Versions Avant Visual Studio 2003

Si vous êtes mise à niveau vers Visual Studio 2010 à partir d’une version avant Visual Studio 2003, vous pouvez voir des erreurs de compilateur liées à la conformité standard améliorée C ' dans Visual Studio 2003

### <a name="upgrading-from-visual-studio-2003"></a>Mise à niveau de Visual Studio 2003

Les projets construits précédemment avec Visual Studio 2003 devraient également être compilés sans **/clr** car Visual Studio a maintenant augmenté la conformité ANSI/ISO et quelques changements de rupture. Le changement qui est susceptible d’exiger le plus d’attention est [caractéristiques de sécurité dans le CRT](../c-runtime-library/security-features-in-the-crt.md). Le code qui utilise le CRT est très susceptible de produire des avertissements de dépréciation. Ces avertissements peuvent être supprimés, mais la migration vers les nouvelles [versions améliorées de sécurité des fonctions CRT](../c-runtime-library/security-enhanced-versions-of-crt-functions.md) est préférable, car ils fournissent une meilleure sécurité et peuvent révéler des problèmes de sécurité dans votre code.

### <a name="upgrading-from-managed-extensions-for-c"></a>Mise à niveau des extensions gérées pour le C

À partir de Visual Studio 2005, le code écrit avec Les extensions gérées pour CMD ne compile pas sous **/clr**.

## <a name="convert-c-code-to-c"></a>Convertir le code C en C

Bien que Visual Studio compile des fichiers C, il est nécessaire de les convertir en CMD pour une compilation **/clr.** Le nom de fichier réel n’a pas besoin d’être changé; vous pouvez utiliser **/Tp** (voir [/Tc, /Tp, /TC, /TP (Specify Source File Type)](../build/reference/tc-tp-tc-tp-specify-source-file-type.md).) Notez que bien que les fichiers de code source CMD soient nécessaires pour **/clr,** il n’est pas nécessaire de re-factorer votre code pour utiliser des paradigmes orientés objet.

Le code C est très susceptible d’exiger des modifications lorsqu’il est compilé sous forme de fichier C. Les règles de sécurité de type CMD sont strictes, de sorte que les conversions de type doivent être explicites avec les moulages. Par exemple, malloc renvoie un pointeur vide, mais peut être attribué à un pointeur à n’importe quel type de C avec un casting:

```
int* a = malloc(sizeof(int));   // C code
int* b = (int*)malloc(sizeof(int));   // C++ equivalent
```

Les pointeurs de fonction sont également strictement de type-sûr dans C, de sorte que le code C suivant nécessite la modification. Dans C, il est préférable `typedef` de créer un qui définit le type de pointeur de fonction, puis d’utiliser ce type pour lancer des pointeurs de fonction:

```
NewFunc1 = GetProcAddress( hLib, "Func1" );   // C code
typedef int(*MYPROC)(int);   // C++ equivalent
NewFunc2 = (MYPROC)GetProcAddress( hLib, "Func2" );
```

Il faut également que les fonctions soient prototypes ou entièrement définies avant qu’elles puissent être référencées ou invoquées.

Les identifiants utilisés dans le code C qui se trouvent être des mots clés dans C (tels que **virtuel**, **nouveau**, **supprimer**, **bool**, **vrai**, **faux,** etc) doivent être renommés. Cela peut généralement se faire par de simples opérations de recherche et de remplacement.

```
COMObj1->lpVtbl->Method(COMObj, args);  // C code
COMObj2->Method(args);  // C++ equivalent
```

## <a name="reconfigure-project-settings"></a>Reconfigurer les paramètres du projet

Après la compilation et l’exécution de votre projet dans Visual Studio 2010, vous devez créer de nouvelles configurations de projets **pour/clr** plutôt que de modifier les configurations par défaut. **/clr** est incompatible avec certaines options de compilateur et la création de configurations séparées vous permet de construire votre projet en tant que natif ou géré. Lorsque **/clr** est sélectionné dans la boîte de dialogue des pages de propriété, les paramètres du projet non compatibles avec **/clr** sont désactivés (et les options désactivées ne sont pas automatiquement restaurées si **/clr** n’est pas sélectionné par la suite).

### <a name="create-new-project-configurations"></a>Créer de nouvelles configurations de projet

Vous pouvez utiliser **copy Paramètres À partir de l’option** dans la nouvelle boîte de dialogue de configuration de **projet** **(Configuration** > **Manager** > **Active Solution Configuration** > **New**) pour créer une configuration de projet basée sur les paramètres de votre projet existant. Faites-le une fois pour la configuration Debug et une fois pour la configuration Dembouctou. Les modifications ultérieures peuvent ensuite être appliquées uniquement aux configurations spécifiques à la **clr,** laissant intactes les configurations de projet d’origine.

Les projets qui utilisent des règles de construction personnalisées peuvent nécessiter une attention particulière.

Cette étape a des implications différentes pour les projets qui utilisent des makefiles. Dans ce cas, une cible de build distincte peut être configurée, ou la version spécifique à la compilation **/clr** peut être créée à partir d’une copie de l’original.

### <a name="change-project-settings"></a>Modifier les paramètres du projet

**/clr** peut être sélectionné dans l’environnement de développement en suivant les instructions en [/clr (Common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md). Comme mentionné précédemment, cette étape désactivera automatiquement les paramètres de projet contradictoires.

> [!NOTE]
> Lors de la mise à niveau d’une bibliothèque gérée ou d’un projet de service Web à partir de Visual Studio 2003, l’option **compilateur /Zl** s’ajoutera à la page de propriété **de la ligne de commandement.** Cela causera LNK2001. Supprimer **/Zl** de la page de propriété de la ligne de **commandement** à résoudre. Voir [/Zl (Omit Default Library Name)](../build/reference/zl-omit-default-library-name.md) et [Set compiler et construire des propriétés](../build/working-with-project-properties.md) pour plus d’informations. Ou, ajoutez msvcrt.lib et msvcmrt.lib à la propriété **de dépendances supplémentaires** du linker.

Pour les projets construits avec des makefiles, les options de compilateur incompatibles doivent être désactivées manuellement une fois **que /clr** est ajouté. Voir /[/clr Restrictions](../build/reference/clr-restrictions.md) pour des informations sur les options de compilateur qui ne sont pas compatibles avec **/clr**.

### <a name="precompiled-headers"></a>En-têtes précompilés

Les en-têtes précompilés sont pris en charge sous **/clr**. Toutefois, si vous ne compilez que certains de vos fichiers du RPC avec **/clr** (compilant le reste en tant que natif), certains changements seront nécessaires parce que les en-têtes précompilés générés avec **/clr** ne sont pas compatibles avec ceux générés sans **/clr**. Cette incompatibilité est due au fait que **/clr** génère et nécessite des métadonnées. Les modules compilés **/clr** ne peuvent donc pas utiliser des en-têtes précompilés qui n’incluent pas les métadonnées, et les modules non **/clr** ne peuvent pas utiliser des fichiers d’en-tête précompilés qui contiennent des données méta.

La façon la plus simple de compiler un projet où certains modules sont compilés **/clr** est de désactiver complètement les en-têtes précomptés. (Dans le dialogue du projet Pages de propriété, ouvrez le nœud C/C et sélectionnez les en-têtes précompilés. Ensuite, modifiez la propriété Créer/Utiliser des en-têtes précompilés en « Ne pas utiliser les en-têtes précompilés ».

Cependant, en particulier pour les grands projets, les en-têtes précompilés offrent une vitesse de compilation beaucoup mieux, de sorte que désactiver cette fonctionnalité n’est pas souhaitable. Dans ce cas, il est préférable de configurer les fichiers **/clr** et non **/clr** pour utiliser des en-têtes précompilés séparés. Cela peut être fait en une seule étape en sélectionnant plusieurs modules à compilés **/clr** à l’aide **de Solution Explorer**, en cliquant à droite sur le groupe, et en sélectionnant les propriétés. Ensuite, modifiez les propriétés De fichier De fichier De création/utilisation et d’en-tête précompilées pour utiliser un nom de fichier d’en-tête différent et un fichier PCH respectivement.

## <a name="fixing-errors"></a>Correction des erreurs

La compilation avec **/clr** peut entraîner des erreurs de compilateur, de liaison ou d’exécution. Cette section traite des problèmes les plus courants.

### <a name="metadata-merge"></a>Fusion de métadonnées

Différentes versions des types de données peuvent faire échouer le linker parce que les métadonnées générées pour les deux types ne correspondent pas. (Cela est habituellement causé lorsque les membres d’un type sont définis sous condition, mais les conditions ne sont pas les mêmes pour tous les fichiers du RPC qui utilisent le type.) Dans ce cas, le lien échoue, ne signalant que le nom du symbole et le nom du deuxième fichier OBJ où le type a été défini. Il est souvent utile de faire pivoter l’ordre que les fichiers OBJ sont envoyés au lienur pour découvrir l’emplacement de l’autre version du type de données.

### <a name="loader-lock-deadlock"></a>Impasse de verrouillage de chargeur

L'« impasse de verrouillage de chargeur » peut se produire, mais elle est déterministe et est détectée et signalée au moment de l’exécution. Voir [Initialisation des assemblées mixtes](../dotnet/initialization-of-mixed-assemblies.md) pour des informations détaillées, des conseils et des solutions.

### <a name="data-exports"></a>Exportations de données

L’exportation de données DLL est sujette aux erreurs et n’est pas recommandée. C’est parce que la section de données d’un DLL n’est pas garanti d’être initialisé jusqu’à ce qu’une partie gérée de la DLL a été exécutée. Métadonnées de référence avec [directive #using](../preprocessor/hash-using-directive-cpp.md).

### <a name="type-visibility"></a>Visibilité du type

Les types autochtones sont privés par défaut. Cela peut entraîner un type natif ne pas être visible en dehors de la DLL. Résoudre cette erreur `public` en ajoutant à ces types.

### <a name="floating-point-and-alignment-issues"></a>Questions de point flottant et d’alignement

`__controlfp`n’est pas pris en charge sur l’heure courante (voir [_control87, _controlfp, \__control87_2](../c-runtime-library/reference/control87-controlfp-control87-2.md) pour plus d’informations). Le CLR ne respectera pas non plus [l’alignement](../cpp/align-cpp.md).

### <a name="com-initialization"></a>Initialisation COM

Le Common Language Runtime initialise AUTOMATIQUEMENT COM lorsqu’un module est parasécé (lorsque COM est parasécisé automatiquement, il est fait comme MTA). Par conséquent, l’initialisation explicite des codes de rendement com indique que com est déjà parastérisée. Tenter d’initialiser explicitement COM avec un modèle de threading lorsque le CLR a déjà paraminé COM à un autre modèle de threading peut provoquer l’échec de votre application.

L’heure courante commence COM comme MTA par défaut; utiliser [/CLRTHREADATTRIBUTE (Set CLR Thread Attribute)](../build/reference/clrthreadattribute-set-clr-thread-attribute.md) pour modifier cela.

### <a name="performance-issues"></a>Problèmes de performance

Vous pouvez voir une diminution des performances lorsque les méthodes natives de CMD générées à MSIL sont appelées indirectement (appels de fonction virtuelle ou à l’aide de pointeurs de fonction). Pour en savoir plus à ce sujet, voir [Double Thunking](../dotnet/double-thunking-cpp.md).

Lorsque vous déménagez d’origine à MSIL, vous remarquerez une augmentation de la taille de votre ensemble de travail. C’est parce que l’heure courante de course de langue fournit de nombreuses fonctionnalités pour s’assurer que les programmes fonctionnent correctement. Si votre application **/clr** n’est pas en cours d’exécution correctement, vous pouvez activer C4793 (off by default), voir [Compiler Warning (niveau 1 et 3) C4793](../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md) pour plus d’informations.

### <a name="program-crashes-on-shutdown"></a>Le programme s’écrase à l’arrêt

Dans certains cas, le CLR peut s’arrêter avant que votre code géré ne soit fini d’être en marche. L’utilisation `std::set_terminate` et `SIGTERM` peut causer cela. Voir [le signal Constants](../c-runtime-library/signal-constants.md) et [set_terminate](../c-runtime-library/abnormal-termination.md) pour plus d’informations.

## <a name="using-new-visual-c-features"></a>Utilisation de nouvelles fonctionnalités Visual CMD

Après que votre application compile, liens, et exécute, vous pouvez commencer à utiliser des fonctionnalités .NET dans n’importe quel module compilé avec **/clr**. Pour plus d’informations, consultez [Extensions de composant pour les plateformes Runtime](../extensions/component-extensions-for-runtime-platforms.md).

Pour plus d’informations sur la programmation .NET dans Visual C ' voir:

- [.NET Programmation avec CMD/CLI (Visual CMD)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

- [Interopérabilité native et .NET](../dotnet/native-and-dotnet-interoperability.md)

- [Extensions de composant pour les plateformes Runtime](../extensions/component-extensions-for-runtime-platforms.md)

## <a name="see-also"></a>Voir aussi

[Assemblys mixtes (natif et managé)](../dotnet/mixed-native-and-managed-assemblies.md)
