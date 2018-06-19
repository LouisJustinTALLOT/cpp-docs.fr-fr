---
title: Exportation et importation à l’aide de AFX_EXT_CLASS | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- afx_ext_class
dev_langs:
- C++
helpviewer_keywords:
- AFX_EXT_CLASS macro
- exporting classes [C++]
- importing DLLs [C++]
- extension DLLs [C++], exporting classes
- executable files [C++], importing classes
- exporting DLLs [C++], AFX_EXT_CLASS macro
ms.assetid: 6b72cb2b-e92e-4ecd-bcab-c335e1d1cfde
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f6cc853c66afae72d6e426d800c0443ab206ab20
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32371058"
---
# <a name="exporting-and-importing-using-afxextclass"></a>Exportation et importation à l'aide de AFX_EXT_CLASS  
  
[DLL d’extension MFC](../build/extension-dlls-overview.md) utiliser la macro **AFX_EXT_CLASS** pour exporter des classes ; les exécutables liés à la DLL d’extension MFC utilisent la macro pour importer des classes. Avec la **AFX_EXT_CLASS** (macro), les fichiers d’en-tête qui sont utilisés pour générer la DLL peut être utilisé avec les exécutables liés à la DLL d’extension MFC.  
  
 Dans le fichier d’en-tête pour votre DLL, ajoutez le **AFX_EXT_CLASS** (mot clé) à la déclaration de votre classe, comme suit :  
  
```cpp  
class AFX_EXT_CLASS CMyClass : public CDocument  
{  
// <body of class>  
};  
```  
  
Cette macro est définie par les MFC en tant que `__declspec(dllexport)` lorsque les symboles de préprocesseur `_AFXDLL` et `_AFXEXT` sont définis. Mais la macro est définie en tant que `__declspec(dllimport)` lorsque `_AFXDLL` est défini et `_AFXEXT` n’est pas défini. Lorsque défini, le symbole de préprocesseur `_AFXDLL` indique que la version partagée de MFC est utilisée par l’exécutable cible (une DLL ou une application). Lorsque les deux `_AFXDLL` et `_AFXEXT` sont définis, cela indique que l’exécutable cible est une DLL d’extension MFC.  
  
Étant donné que `AFX_EXT_CLASS` est défini comme `__declspec(dllexport)` lors de l’exportation à partir d’une DLL d’extension MFC, vous pouvez exporter des classes entières sans placer les noms décorés de tous les symboles de la classe dans le fichier .def.  
  
Bien que vous pouvez éviter la création d’un fichier .def et tous les noms décorés de la classe avec cette méthode, la création d’un fichier .def est plus efficace car les noms peuvent être exportés par ordinal. Pour utiliser la méthode de fichier .def d’exportation, placez le code suivant au début et à la fin du fichier d’en-tête :  
  
```cpp  
#undef AFX_DATA  
#define AFX_DATA AFX_EXT_DATA  
// <body of your header file>  
#undef AFX_DATA  
#define AFX_DATA  
```  
  
> [!CAUTION]
>  Soyez prudent lors de l’exportation de fonctions inline, car elles peuvent donner lieu à des conflits de versions. Une fonction inline est développée en code d’application ; Par conséquent, si vous réécrivez ultérieurement la fonction, il ne pas mis à jour, sauf si l’application elle-même est recompilée. Normalement, DLL (fonctions) peuvent être mis à jour sans régénération des applications qui les utilisent.  
  
## <a name="exporting-individual-members-in-a-class"></a>Exportation de membres individuels dans une classe  
  
Vous pouvez parfois exporter des membres individuels de votre classe. Par exemple, si vous exportez un `CDialog`-classe dérivée, vous devrez peut-être uniquement exporter le constructeur et le `DoModal` appeler. Vous pouvez utiliser `AFX_EXT_CLASS` sur les membres individuels, vous devez exporter.  
  
Par exemple :  
  
```cpp  
class CExampleDialog : public CDialog  
{  
public:  
   AFX_EXT_CLASS CExampleDialog();  
   AFX_EXT_CLASS int DoModal();  
   ...  
   // rest of class definition  
   ...  
};  
```  
  
Étant donné que vous n’exportez plus tous les membres de la classe, vous pouvez exécuter dans un autre problème en raison du mode fonctionnement des macros MFC. Plusieurs macros d’assistance MFC réellement déclarent ou définissent des membres de données. Par conséquent, ces membres de données doivent également être exportées à partir de votre DLL.  
  
Par exemple, le `DECLARE_DYNAMIC` macro est défini comme suit lors de la création d’une DLL d’extension MFC :  
  
```cpp  
#define DECLARE_DYNAMIC(class_name) \  
protected: \  
   static CRuntimeClass* PASCAL _GetBaseClass(); \  
public: \  
   static AFX_DATA CRuntimeClass class##class_name; \  
   virtual CRuntimeClass* GetRuntimeClass() const; \  
```  
  
La ligne qui commence par statique `AFX_DATA` déclare un objet statique à l’intérieur de votre classe. Pour exporter cette classe correctement et accéder aux informations d’exécution à partir d’un fichier exécutable du client, vous devez exporter cet objet statique. Car l’objet statique est déclaré avec le modificateur `AFX_DATA`, vous ne devez définir `AFX_DATA` être `__declspec(dllexport)` lors de la création de la DLL et définir en tant que `__declspec(dllimport)` lors de la génération de l’exécutable client. Étant donné que `AFX_EXT_CLASS` est déjà définie de cette façon, il vous suffit de redéfinir `AFX_DATA` pour être le même que `AFX_EXT_CLASS` autour de votre définition de classe.  
  
Par exemple :  
  
```cpp  
#undef  AFX_DATA  
#define AFX_DATA AFX_EXT_CLASS  
  
class CExampleView : public CView  
{  
   DECLARE_DYNAMIC()  
   // ... class definition ...  
};  
  
#undef  AFX_DATA  
#define AFX_DATA  
```  
  
Étant donné que MFC utilise toujours le `AFX_DATA` symbole sur les éléments de données qu’elles définissent dans leurs macros, cette technique fonctionne pour tous ces scénarios. Par exemple, il fonctionne pour `DECLARE_MESSAGE_MAP`.  
  
> [!NOTE]
>  Si vous exportez la classe entière plutôt que les membres sélectionnés de la classe, les données membres statiques sont exportés automatiquement.  
  
### <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?  
  
-   [Exporter à partir d’une DLL à l’aide de fichiers .def](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Exporter à partir d’une DLL à l’aide de __declspec (dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Exporter des fonctions C++ à utiliser dans des exécutables en langage C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Exporter des fonctions C à utiliser dans des exécutables en langage C ou C++](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [Déterminer la méthode d’exportation à utiliser](../build/determining-which-exporting-method-to-use.md)  
  
-   [Importer dans une application à l’aide de __declspec (dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [Initialiser une DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
### <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?  
  
-   [Noms décorés](../build/reference/decorated-names.md)  
  
-   [Importation et exportation de fonctions inline](../build/importing-and-exporting-inline-functions.md)  
  
-   [Importations mutuelles](../build/mutual-imports.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exportation à partir d’une DLL](../build/exporting-from-a-dll.md)