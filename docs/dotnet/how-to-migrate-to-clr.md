---
title: 'Comment : migrer vers - clr | Documents Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- upgrading Visual C++ applications, /clr compiler option
- compiling native code [C++]
- interoperability [C++], /clr compiler option
- interop [C++], /clr compiler option
- migration [C++], /clr compiler option
- /clr compiler option [C++], porting to
ms.assetid: c9290b8b-436a-4510-8b56-eae51f4a9afc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f5d7dafdc377723e33372529af1b8f125561366e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33138438"
---
# <a name="how-to-migrate-to-clr"></a>Comment : effectuer une migration vers /clr
Cette rubrique traite des problèmes qui surviennent lors de la compilation de code natif avec **/CLR** (consultez [/clr (Compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) pour plus d’informations). **/ CLR** permet de modules Visual C++ d’appeler et d’être appelés depuis les assemblys .NET tout en conservant la compatibilité avec les modules non managés. Consultez [mixte (natif et managé) assemblys](../dotnet/mixed-native-and-managed-assemblies.md) et [natif et l’interopérabilité .NET](../dotnet/native-and-dotnet-interoperability.md) pour plus d’informations sur les avantages de la compilation avec **/CLR**.  
  
## <a name="known-issues-compiling-library-projects-with-clr"></a>Connus problèmes de la compilation de projets de bibliothèque avec/CLR  
 Visual Studio contient des problèmes connus lors de la compilation de projets de bibliothèque avec **/CLR**:  
  
-   Votre code peut interroger des types pendant l’exécution avec [CRuntimeClass::FromName](../mfc/reference/cruntimeclass-structure.md#fromname). Toutefois, si un type est dans un fichier .dll MSIL (compilé avec **/CLR**), l’appel à `FromName` risque d’échouer si elle se produit avant l’exécution des constructeurs statiques dans le .dll managé (vous ne verrez pas ce problème si l’appel FromName se produit une fois que le code a exécutée dans le .dll managé). Pour contourner ce problème, vous pouvez forcer la construction du constructeur statique managé en définissant une fonction dans la DLL managée, exportant et appeler à partir d’une application MFC native. Par exemple :  
  
    ```  
    // MFC extension DLL Header file:  
    __declspec( dllexport ) void EnsureManagedInitialization () {  
       // managed code that won't be optimized away  
       System::GC::KeepAlive(System::Int32::MaxValue);  
    }  
    ```  
  
## <a name="compile-with-visual-c"></a>Compilation avec Visual C++  
 Avant d’utiliser **/CLR** sur n’importe quel module dans votre projet, vous devez d’abord compiler et lier votre projet natif avec Visual Studio 2010.  
  
 Les étapes suivantes, suivies dans l’ordre, fournissent le chemin d’accès plus facile à un **/CLR** compilation. Il est important de compiler et exécuter votre projet après chacune de ces étapes.  
  
### <a name="versions-prior-to-visual-c-2003"></a>Versions antérieures à Visual C++ 2003  
 Si vous mettez à niveau vers Visual Studio 2010 à partir d’une version antérieure de Visual C++ 2003, vous pouvez voir les erreurs de compilation liées à la meilleure conformité standard C++ dans Visual C++ 2003  
  
### <a name="upgrading-from-visual-c-2003"></a>La mise à niveau à partir de Visual C++ 2003  
 Projets antérieurs générés avec Visual C++ 2003 doivent également être compilés d’abord sans **/CLR** que Visual Studio bénéficie d’une meilleure mise en conformité ANSI/ISO et des modifications avec rupture. La modification est susceptible de demander le plus d’attention est [les fonctionnalités de sécurité dans la bibliothèque CRT](../c-runtime-library/security-features-in-the-crt.md). Le code qui utilise la bibliothèque CRT est très probable produire des avertissements de désapprobation. Ces avertissements peuvent être supprimés, mais la migration vers le nouveau [Versions de fonctions CRT](../c-runtime-library/security-enhanced-versions-of-crt-functions.md) est recommandée, car ils fournissent une meilleure sécurité et peuvent révéler des problèmes de sécurité dans votre code.  
  
### <a name="upgrading-from-managed-extensions-for-c"></a>La mise à niveau à partir des Extensions managées pour C++  
 À compter de Visual Studio 2005, le code écrit avec les Extensions managées pour C++ ne compilera pas sous **/CLR**.  
  
## <a name="convert-c-code-to-c"></a>Convertir le Code C en C++  
 Bien que Visual Studio puisse compiler des fichiers C, il est nécessaire de les convertir en C++ pour une **/CLR** compilation. Nom de fichier ne doit pas être modifié ; Vous pouvez utiliser **/Tp** (consultez [/Tc, / TP, /TP (spécifier le Type des fichiers Source)](../build/reference/tc-tp-tc-tp-specify-source-file-type.md).) Notez que bien que les fichiers de code source C++ sont requis pour **/CLR**, il n’est pas nécessaire de refactoriser votre code pour utiliser des paradigmes orientés objet.  
  
 Code C est très susceptible de nécessiter des modifications lors de la compilation dans un fichier C++. Les règles de sécurité de type C++ étant stricts, les conversions de type doivent être explicites à des casts. Par exemple, malloc retourne un pointeur void, mais peut être assigné à un pointeur vers n’importe quel type en C avec un cast :  
  
```  
int* a = malloc(sizeof(int));   // C code  
int* b = (int*)malloc(sizeof(int));   // C++ equivalent  
```  
  
 Pointeurs fonction sont aussi strictement de type sécurisé en C++, le code C suivant nécessite la modification. En C++, il est préférable de créer un `typedef` qui définit le type de pointeur de fonction, puis utiliser ce type pour convertir des pointeurs de fonction :  
  
```  
NewFunc1 = GetProcAddress( hLib, "Func1" );   // C code  
typedef int(*MYPROC)(int);   // C++ equivalent  
NewFunc2 = (MYPROC)GetProcAddress( hLib, "Func2" );  
```  
  
 C++ requiert également être soit prototypée soit complètement définie avant de pouvoir être référencées ou appelées.  
  
 Les identificateurs utilisés dans le code C qui se trouvent les mots clés en C++ (tels que `virtual`, `new`, `delete`, `bool`, `true`, `false`, etc.) doit être renommé. Généralement procéder aux opérations de recherche et remplacement simples.  
  
 Enfin, tandis que les appels COM de style C requièrent l’utilisation explicite de la v-table et `this` pointeur, C++ n’est pas :  
  
```  
COMObj1->lpVtbl->Method(COMObj, args);  // C code  
COMObj2->Method(args);  // C++ equivalent  
```  
  
## <a name="reconfigure-project-settings"></a>Reconfigurer les paramètres de projet  
 Une fois que votre projet se compile et s’exécute dans Visual Studio 2010, vous devez créer des configurations de projet pour **/CLR** plutôt que de modifier les configurations par défaut. **/ CLR** n’est pas compatible avec certaines options du compilateur et la création de configurations séparées vous permet de générer votre projet comme natif ou managé. Lorsque **/CLR** est sélectionné dans la boîte de dialogue des pages de propriété, des paramètres de projet non compatibles avec **/CLR** sont désactivées (et les options désactivées ne sont pas automatiquement restaurées si   **/CLR** est désélectionné par la suite).  
  
### <a name="create-new-project-configurations"></a>Créer des Configurations de projet  
 Vous pouvez utiliser **copier les paramètres de** option dans le [nouvelle boîte de dialogue de Configuration de projet](http://msdn.microsoft.com/en-us/cca616dc-05a6-4fe3-bdc1-40c72a66f2be) pour créer une configuration de projet en fonction de vos paramètres de projet existants. Faire une fois pour la configuration Debug et une fois pour la configuration Release. Les modifications ultérieures peuvent ensuite être appliquées à la **/CLR** -configurations spécifiques uniquement, toucher les configurations de projet d’origine.  
  
 Les projets qui utilisent des règles de génération personnalisée peuvent nécessiter une attention particulière.  
  
 Cette étape a différentes implications pour les projets qui utilisent des makefiles. Dans ce cas une cible de génération distincte peut être configurée, ou une version spécifique de **/CLR** compilation peut être créée à partir d’une copie de l’original.  
  
### <a name="change-project-settings"></a>Modifier les paramètres de projet  
 **/ CLR** peut être sélectionné dans l’environnement de développement en suivant les instructions de [/clr (Compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md). Comme mentionné précédemment, cette étape désactivera automatiquement les paramètres de projet en conflit.  
  
> [!NOTE]
>  Lors de la mise à niveau d’une bibliothèque managée ou un projet de service web à partir de Visual C++ 2003, les **/Zl** est d’option du compilateur ajoutée dans le **ligne de commande** page de propriétés. Cela provoquera une erreur LNK2001. Supprimer **/Zl** à partir de la **ligne de commande** page de propriétés. Consultez [/Zl (omettre les nom de bibliothèque par défaut)](../build/reference/zl-omit-default-library-name.md) et [utilisation des propriétés de projet](../ide/working-with-project-properties.md) pour plus d’informations. Ou ajoutez msvcrt.lib et msvcmrt.lib à l’éditeur de liens **dépendances supplémentaires** propriété.  
  
 Pour les projets générés avec des makefiles, les options du compilateur incompatibles doivent être désactivées manuellement une fois **/CLR** est ajouté. Consultez /[Restrictions de /clr](../build/reference/clr-restrictions.md) pour plus d’informations sur les options du compilateur qui ne sont pas compatibles avec **/CLR**.  
  
### <a name="precompiled-headers"></a>En-têtes précompilés  
 Les en-têtes précompilés sont pris en charge sous **/CLR**. Toutefois, si vous ne compilez que certains de vos fichiers CPP avec **/CLR** (en compilant le reste en natif) des modifications sera nécessaire, car les en-têtes précompilés générés avec **/CLR** ne sont pas compatibles avec ceux généré sans **/CLR**. Cette incompatibilité est due au fait que **/CLR** génère et requiert des métadonnées. Modules compilés **/CLR** ne peuvent donc pas utiliser des en-têtes précompilés qui n’incluent pas de métadonnées et non **/CLR** modules ne peuvent pas utiliser les fichiers d’en-tête précompilés qui contiennent des métadonnées.  
  
 Le moyen le plus simple de compiler un projet dont certains modules sont compilés **/CLR** consiste à désactiver complètement les en-têtes précompilés. (Dans la boîte de dialogue Pages de propriétés du projet, ouvrez le nœud C/C++ et sélectionnez les en-têtes précompilés. Puis remplacez la propriété d’en-têtes précompilés de création/utilisation « Pas utiliser les en-têtes précompilés ».)  
  
 Toutefois, en particulier pour les projets volumineux, les en-têtes précompilés fournissent beaucoup plus rapide de la compilation, afin de désactiver cette fonctionnalité n’est pas souhaitable. Dans ce cas, il est préférable de configurer le **/CLR** et non **/CLR** fichiers à utiliser séparément les en-têtes précompilés. Cela est possible en une seule étape en vous sélectionnez plusieurs modules à compiler **/CLR** à l’aide de l’Explorateur de solutions, en cliquant sur le groupe et en sélectionnant Propriétés. Puis modifier les propriétés de la création/utilisation via aucun fichier PCH et le fichier d’en-tête précompilé pour utiliser un nom de fichier d’en-tête et le fichier PCH respectivement.  
  
## <a name="fixing-errors"></a>Correction des erreurs  
 La compilation avec **/CLR** peut provoquer des erreurs du compilateur, l’éditeur de liens ou runtime. Cette section traite des problèmes les plus courants.  
  
### <a name="metadata-merge"></a>Fusion des métadonnées  
 Différentes versions des types de données risque d’échouer car les métadonnées générées pour les deux types ne correspond pas à l’éditeur de liens. (Il s’agit généralement lorsque les membres d’un type sont définis de façon conditionnelle, mais les conditions ne sont pas les mêmes pour tous les fichiers CPP qui utilisent le type.) Dans ce cas l’éditeur de liens échoue uniquement le nom du symbole et le nom du deuxième fichier OBJ où le type a été défini. Il est souvent utile d’inverser l’ordre que les fichiers OBJ sont envoyés à l’éditeur de liens pour découvrir l’emplacement de l’autre version du type de données.  
  
### <a name="loader-lock-deadlock"></a>Blocage du verrouillage du chargeur  
 Dans Visual Studio 2010 et versions ultérieures, le « blocage de verrouillage du chargeur » peut encore se produire que dans les versions antérieures, mais elle est déterministe et détectées et signalées lors de l’exécution. Consultez [l’initialisation d’assemblys mixtes](../dotnet/initialization-of-mixed-assemblies.md) pour des informations détaillées, des conseils et solutions.  
  
### <a name="data-exports"></a>Exportations de données  
 Exportation de données de la DLL est déconseillé et sujette à erreurs. Il s’agit, car la section de données d’une DLL n’est pas garantie d’être initialisée avant qu’une partie managée de la DLL a été exécutée. Les métadonnées de référence avec [#using, Directive](../preprocessor/hash-using-directive-cpp.md).  
  
### <a name="type-visibility"></a>Visibilité du type  
 Les types natifs sont privés par défaut. Cela peut entraîner un type natif ne sont pas visibles en dehors de la DLL. Résoudre cette erreur en ajoutant `public` à ces types.  
  
### <a name="floating-point-and-alignment-issues"></a>Virgule flottante et problèmes d’alignement  
 `__controlfp` n’est pas pris en charge sur le common language runtime (consultez [_control87, _controlfp, \__control87_2](../c-runtime-library/reference/control87-controlfp-control87-2.md) pour plus d’informations). Le CLR ne respecte également [aligner](../cpp/align-cpp.md).  
  
### <a name="com-initialization"></a>Initialisation de COM  
 Le Common Language Runtime initialise automatiquement COM lorsqu’un module est initialisé (lorsque COM est initialisé automatiquement qu’il a effectué cette opération en tant que MTA). Par conséquent, initialiser COM explicitement génère des codes de retour qui indique que COM est déjà initialisé. Tentative d’initialisation explicite de COM avec un modèle de thread lorsque le CLR a déjà initialisé COM vers un autre modèle de thread peut provoquer l’échec de votre application.  
  
 Le common language runtime démarre COM en tant que MTA par défaut ; Utilisez [/CLRTHREADATTRIBUTE (Set CLR Thread Attribute)](../build/reference/clrthreadattribute-set-clr-thread-attribute.md) pour modifier cela.  
  
### <a name="performance-issues"></a>Problèmes de performances  
 Vous pouvez voir une diminution des performances lorsque les méthodes C++ natives générées en MSIL sont appelées indirectement (appels de fonction virtuelle ou à l’aide de pointeurs de fonction). Pour plus d’informations, consultez [Double médiateur](../dotnet/double-thunking-cpp.md).  
  
 Lors du déplacement du code natif en langage MSIL, vous pouvez remarquer une augmentation de la taille de votre jeu de travail. Il s’agit, car le common language runtime fournit de nombreuses fonctionnalités pour vous assurer que les programmes s’exécutent correctement. Si votre **/CLR** application ne fonctionne pas correctement, vous pouvez activer C4793 (désactivé par défaut), consultez [l’avertissement du compilateur (niveau 1 et 3) C4793](../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md) pour plus d’informations.  
  
### <a name="program-crashes-on-shutdown"></a>Incidents de programme lors de l’arrêt  
 Dans certains cas, le CLR peut quitter avant la fin de votre code managé en cours d’exécution. À l’aide de `std::set_terminate` et `SIGTERM` peuvent entraîner ce problème. Consultez [signal, constantes](../c-runtime-library/signal-constants.md) et [set_terminate](../c-runtime-library/abnormal-termination.md) pour plus d’informations.  
  
## <a name="using-new-visual-c-features"></a>À l’aide des nouvelles fonctionnalités de Visual C++  
 Une fois votre application compilée, les liens et s’exécute, vous pouvez commencer à l’aide des fonctionnalités .NET dans n’importe quel module compilé avec **/CLR**. Pour plus d’informations, consultez [Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md).  
  
 Si vous avez utilisé des Extensions managées pour C++, vous pouvez convertir votre code pour utiliser la nouvelle syntaxe. Pour plus d’informations sur la conversion d’Extensions managées pour C++, consultez [C + c++ / CLI Migration Primer](../dotnet/cpp-cli-migration-primer.md).  
  
 Pour plus d’informations sur la programmation dans Visual C++ .NET, consultez :  
  
-   [Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)  
  
-   [Interopérabilité native et .NET](../dotnet/native-and-dotnet-interoperability.md)  
  
-   [Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Assemblys mixtes (natif et managé)](../dotnet/mixed-native-and-managed-assemblies.md)