---
title: "/EXPORTS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/exports"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/EXPORTS (option Dumpbin)"
  - "EXPORTS (option Dumpbin)"
  - "-EXPORTS (option Dumpbin)"
ms.assetid: dbcd7579-b855-44c4-bd27-931e157657f7
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# EXPORTS
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Introduit une section d'une ou plusieurs définitions d'exportation qui spécifient les ordinaux ou noms exportés des fonctions ou données.  Chaque définition doit être sur une ligne distincte.  
  
```  
EXPORTS  
   definition  
```  
  
## Notes  
 La première `definition` peut être sur la même ligne que le mot clé `EXPORTS` ou sur une ligne suivante.  Le fichier .DEF peut contenir une ou plusieurs instructions `EXPORTS`.  
  
 La syntaxe d'une `definition` d'exportation est :  
  
```  
  
entryname[=internalname] [@ordinal [NONAME]] [[PRIVATE] | [DATA]]  
```  
  
 `entryname` est le nom de la variable ou de la fonction que vous voulez exporter.  Cet élément est obligatoire.  Si le nom que vous exportez diffère du nom figurant dans la DLL, spécifiez le nom de l'exportation dans la DLL en utilisant `internalname`.  Par exemple, si votre DLL exporte une fonction `func1` et que vous voulez que les appelants l'utilisent comme `func2`, vous devez spécifier :  
  
```  
EXPORTS  
   func2=func1  
```  
  
 Comme le compilateur Visual C\+\+ utilise la décoration de nom pour les fonctions C\+\+, vous devez utiliser le nom décoré comme `entryname` ou `internalname`, ou définir les fonctions exportées en utilisant `extern "C"` dans le code source.  Le compilateur décore également les fonctions C qui utilisent la convention d'appel [\_\_stdcall](../../cpp/stdcall.md) avec un trait de soulignement \(\_\) en préfixe et avec un suffixe composé d'un arobase \(@\) suivi du nombre d'octets \(au format décimal\) dans la liste d'arguments.  
  
 Pour rechercher les noms décorés produits par le compilateur, utilisez l'outil [DUMPBIN](../../build/reference/dumpbin-reference.md) ou l'option [\/MAP](../../build/reference/map-generate-mapfile.md) de l'éditeur de liens.  Les noms décorés sont spécifiques au compilateur.  Si vous exportez les noms décorés dans le fichier .DEF, les exécutables qui sont liés à la DLL doivent également être générés à l'aide la même version du compilateur.  Cela garantit que les noms décorés dans l'appelant correspondent aux noms exportés dans le fichier .DEF.  
  
 Vous pouvez utiliser @`ordinal` pour spécifier qu'un nombre, et non pas le nom de la fonction, soit placé dans la table d'exportation de la DLL.  De nombreuses DLL Windows exportent des ordinaux pour prendre en charge du code hérité.  Il était courant d'utiliser des ordinaux dans le code Windows 16 bits, car cela peut aider à réduire la taille d'une DLL.  Nous ne conseillons pas l'exportation de fonctions par ordinal à moins que vos clients de DLL en aient besoin pour une prise en charge héritée.  Comme le fichier .LIB contiendra le mappage entre l'ordinal et la fonction, vous pouvez utiliser le nom de fonction comme vous le feriez normalement dans les projets qui utilisent la DLL.  
  
 En utilisant le mot clé `NONAME` facultatif, vous pouvez exporter par ordinal uniquement et réduire la taille de la table d'exportation dans la DLL résultante.  Toutefois, si vous voulez utiliser [GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212.aspx) sur la DLL, vous devez connaître l'ordinal car le nom ne sera pas valide.  
  
 Le mot clé facultatif `PRIVATE` empêche `entryname` d'être inclus dans la bibliothèque d'importation générée par LINK.  Il n'affecte pas l'exportation dans l'image également générée par LINK.  
  
 Le mot clé facultatif `DATA` spécifie qu'une exportation se rapporte à des données et non pas à du code.  Cet exemple illustre comment vous pouvez exporter une variable de données nommée `exported_global` :  
  
```  
EXPORTS  
   exported_global DATA  
```  
  
 Il existe quatre méthodes pour exporter une définition, répertoriées dans l'ordre recommandé :  
  
1.  Le mot clé [\_\_declspec\(dllexport\)](../../cpp/dllexport-dllimport.md) dans le code source  
  
2.  Une instruction `EXPORTS` dans un fichier .DEF  
  
3.  Une spécification [\/EXPORT](../../build/reference/export-exports-a-function.md) dans une commande LINK  
  
4.  Une directive [comment](../../preprocessor/comment-c-cpp.md) dans le code source, de la forme `#pragma comment(linker, "/export:``definition``")`  
  
 Ces quatre méthodes peuvent être utilisées dans le même programme.  Quand LINK génère un programme qui contient des exportations, il crée également une bibliothèque d'importation, à moins qu'un fichier .EXP soit utilisé dans la build.  
  
 Voici un exemple de section EXPORTS :  
  
```  
EXPORTS  
   DllCanUnloadNow      @1          PRIVATE  
   DllWindowName = WindowName       DATA  
   DllGetClassObject    @4 NONAME   PRIVATE  
   DllRegisterServer    @7  
   DllUnregisterServer  
```  
  
 Quand vous exportez une variable à partir d'une DLL en utilisant un fichier .DEF, vous n'êtes pas tenu de spécifier `__declspec(dllexport)` sur la variable.  Toutefois, dans tout fichier qui utilise la DLL, vous devez encore utiliser `__declspec(dllimport)` sur la déclaration des données.  
  
## Voir aussi  
 [Règles s'appliquant aux instructions de définition de module](../../build/reference/rules-for-module-definition-statements.md)