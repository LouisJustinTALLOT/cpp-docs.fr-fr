---
description: 'En savoir plus sur : TN058 : implémentation de l’état du module MFC'
title: "TN058 : implémentation de l'état du module MFC"
ms.date: 06/28/2018
helpviewer_keywords:
- thread state [MFC]
- module states [MFC], managing state data
- TN058
- MFC, managing state data
- module states [MFC], switching
- DLLs [MFC], module states
- process state [MFC]
ms.assetid: 72f5b36f-b3da-4009-a144-24258dcd2b2f
ms.openlocfilehash: c4b300b9aa184e9fa1c6cfd5a8cf668d163d85ef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214778"
---
# <a name="tn058-mfc-module-state-implementation"></a>TN058 : implémentation de l'état du module MFC

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note technique décrit l’implémentation des constructions MFC « État du module ». La compréhension de l’implémentation de l’état du module est essentielle pour l’utilisation des DLL partagées MFC à partir d’une DLL (ou d’un serveur OLE in-process).

Avant de lire cette note, reportez-vous à « gestion des données d’état des modules MFC » dans [création de documents, fenêtres et vues](../mfc/creating-new-documents-windows-and-views.md). Cet article contient des informations importantes sur l’utilisation et des informations générales sur ce sujet.

## <a name="overview"></a>Vue d’ensemble

Il existe trois types d’informations d’État MFC : état du module, état du processus et état du thread. Parfois, ces types d’États peuvent être combinés. Par exemple, les mappages de handle MFC sont à la fois de module local et de thread local. Cela permet à deux modules différents d’avoir des mappages différents dans chacun de leurs threads.

L’état du processus et l’état du thread sont similaires. Ces éléments de données sont des éléments qui ont traditionnellement été des variables globales, mais qui doivent être spécifiques à un processus ou à un thread donné pour la prise en charge de Win32s ou pour la prise en charge du multithreading approprié. La catégorie d’un élément de données donné dépend de cet élément et de sa sémantique souhaitée en ce qui concerne les limites des processus et des threads.

L’état du module est unique dans la mesure où il peut contenir soit un état global, soit un état de processus local ou de thread local. En outre, il peut être basculé rapidement.

## <a name="module-state-switching"></a>Changement d’État du module

Chaque thread contient un pointeur vers l’état du module « actif » ou « actif » (pas étonnamment, le pointeur fait partie de l’état local des threads MFC). Ce pointeur est modifié lorsque le thread d’exécution passe une limite de module, telle qu’une application qui appelle un contrôle OLE ou une DLL, ou un contrôle OLE rappelant dans une application.

L’état du module actuel est basculé en appelant `AfxSetModuleState` . Pour l’essentiel, vous ne traiterez jamais directement l’API. MFC, dans de nombreux cas, l’appellera pour vous (à WinMain, point d’entrée OLE, `AfxWndProc` , etc.). Cela est fait dans tout composant que vous écrivez en établissant une liaison statique dans un spécial `WndProc` et un spécial `WinMain` (ou `DllMain` ) qui sait quel état de module doit être actuel. Vous pouvez voir ce code en regardant DLLMODUL. CPP ou APPMODUL. CPP dans le répertoire MFC\SRC.

Il est rare que vous souhaitiez définir l’état du module et ne pas le redéfinir. La plupart du temps, vous souhaitez « pousser » votre propre état de module en cours, puis, une fois terminé, « dépiler » le contexte d’origine. Cette opération est effectuée par la macro [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) et la classe spéciale `AFX_MAINTAIN_STATE` .

`CCmdTarget` possède des fonctionnalités spéciales pour la prise en charge du basculement d’État du module. En particulier, a `CCmdTarget` est la classe racine utilisée pour OLE Automation et les points d’entrée OLE com. Comme tout autre point d’entrée exposé au système, ces points d’entrée doivent définir un état de module correct. Comment est-ce que le fait de `CCmdTarget` savoir quel est l’état du module « correct » doit être la réponse est qu’il « se souvient » de l’état du module « actuel » lorsqu’il est construit, de telle sorte qu’il peut définir l’état du module actuel sur cette valeur « mémorisée » lorsqu’il est appelé par la suite. Par conséquent, l’état du module auquel un `CCmdTarget` objet donné est associé est l’état du module qui était en cours lors de la construction de l’objet. Prenons un exemple simple de chargement d’un serveur INPROC, de création d’un objet et d’appel de ses méthodes.

1. La DLL est chargée par OLE à l’aide de `LoadLibrary` .

1. `RawDllMain` est appelé en premier. Elle définit l’état du module sur l’état du module statique connu pour la DLL. Pour cette raison `RawDllMain` , est lié de manière statique à la dll.

1. Le constructeur pour la fabrique de classe associée à notre objet est appelé. `COleObjectFactory` est dérivée de `CCmdTarget` et par conséquent, il se souvient de l’état du module dans lequel il a été instancié. Cela est important : lorsque la fabrique de classe est invitée à créer des objets, elle sait à présent l’état du module à rendre actuel.

1. `DllGetClassObject` est appelé pour obtenir la fabrique de classe. MFC recherche dans la liste des fabriques de classes associée à ce module et la retourne.

1. La méthode `COleObjectFactory::XClassFactory2::CreateInstance` est appelée. Avant de créer l’objet et de le retourner, cette fonction définit l’état du module à l’état du module actuel à l’étape 3 (celui qui était en cours lorsque le `COleObjectFactory` a été instancié). Cette opération s’effectue à l’intérieur de [METHOD_PROLOGUE](com-interface-entry-points.md).

1. Lorsque l’objet est créé, il est également un `CCmdTarget` dérivé et, de la même façon, le fait de `COleObjectFactory` mémoriser l’état du module était actif, donc ce nouvel objet. À présent, l’objet sait quel état de module passer à chaque fois qu’il est appelé.

1. Le client appelle une fonction sur l’objet OLE COM qu’il a reçu à partir de son `CoCreateInstance` appel. Lorsque l’objet est appelé, il utilise `METHOD_PROLOGUE` pour changer l’état du module comme c’est le cas `COleObjectFactory` .

Comme vous pouvez le voir, l’état du module est propagé d’un objet à l’objet lors de sa création. Il est important que l’état du module soit défini correctement. S’il n’est pas défini, votre DLL ou objet COM peut interagir mal avec une application MFC qui l’appelle, ou il peut ne pas trouver ses propres ressources, ou peut échouer d’autres façons pénible.

Notez que certains types de dll, en particulier les dll d’extension MFC, ne basculent pas l’état du module dans leur `RawDllMain` (en fait, ils n’ont généralement pas de `RawDllMain` ). Cela est dû au fait que les utilisateurs sont censés se comporter comme s’ils étaient réellement présents dans l’application qui les utilise. Ils sont très bien intégrés à l’application en cours d’exécution et il est leur intention de modifier l’état global de l’application.

Les contrôles OLE et les autres dll sont très différents. Ils ne souhaitent pas modifier l’état de l’application appelante ; l’application qui les appelle peut ne pas être une application MFC et, par conséquent, il est possible qu’il n’y ait aucun État à modifier. C’est la raison pour laquelle le basculement de l’état du module a été inventé.

Pour les fonctions exportées à partir d’une DLL, telle que celle qui lance une boîte de dialogue dans votre DLL, vous devez ajouter le code suivant au début de la fonction :

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState())
```

Cela permute l’état du module actuel avec l’état retourné par [AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate) jusqu’à la fin de la portée actuelle.

Les problèmes liés aux ressources dans les dll se produisent si la macro AFX_MODULE_STATE n’est pas utilisée. Par défaut, MFC utilise le handle de ressource d'application principale pour charger le modèle de ressources. Ce modèle est réellement enregistré dans la DLL. La cause première est que les informations d’État du module MFC n’ont pas été basculées par la macro AFX_MODULE_STATE. Le handle de ressources est récupéré de l'état du module MFC. Ne pas afficher l'état du module provoque l'utilisation du mauvais handle de ressource.

AFX_MODULE_STATE n’a pas besoin d’être placé dans chaque fonction dans la DLL. Par exemple, `InitInstance` peut être appelé par le code MFC dans l’application sans AFX_MODULE_STATE, car MFC déplace automatiquement l’état du module avant `InitInstance` , puis le replace après le `InitInstance` retour de. Il en va de même pour tous les gestionnaires de la table des messages. Les DLL MFC normales disposent en fait d’une procédure de fenêtre principale spéciale qui change automatiquement l’état du module avant de router les messages.

## <a name="process-local-data"></a>Traiter les données locales

Le processus de traitement des données locales n’aurait pas été un problème intéressant, car il ne s’agissait pas de la difficulté du modèle DLL Win32s. Dans Win32s, toutes les dll partagent leurs données globales, même lorsqu’elles sont chargées par plusieurs applications. C’est très différent du modèle de données de DLL Win32 « réel », où chaque DLL obtient une copie distincte de son espace de données dans chaque processus qui s’attache à la DLL. Pour ajouter à la complexité, les données allouées sur le tas dans une DLL Win32s sont en fait des processus spécifiques (au moins en ce qui concerne la propriété). Considérez les données et le code suivants :

```cpp
static CString strGlobal; // at file scope

__declspec(dllexport)
void SetGlobalString(LPCTSTR lpsz)
{
    strGlobal = lpsz;
}

__declspec(dllexport)
void GetGlobalString(LPCTSTR lpsz, size_t cb)
{
    StringCbCopy(lpsz, cb, strGlobal);
}
```

Réfléchissez à ce qui se passe si le code ci-dessus se trouve dans une DLL et que cette DLL est chargée par deux processus A et B (il peut en fait s’agir de deux instances de la même application). Appelle `SetGlobalString("Hello from A")` . Par conséquent, la mémoire est allouée pour les `CString` données dans le contexte du processus a. n’oubliez pas que le `CString` lui-même est global et qu’il est visible à la fois pour a et B. À présent, B appelle `GetGlobalString(sz, sizeof(sz))` . B sera en mesure de voir les données d’un jeu. Cela est dû au fait que Win32s n’offre aucune protection entre les processus tels que Win32. C’est le premier problème ; dans de nombreux cas, il n’est pas souhaitable qu’une application affecte les données globales qui sont considérées comme appartenant à une application différente.

Il existe également des problèmes supplémentaires. Supposons qu’un s’arrête maintenant. Lorsqu’un se termine, la mémoire utilisée par la `strGlobal` chaîne' 'est rendue disponible pour le système, c’est-à-dire que toute la mémoire allouée par le processus a est automatiquement libérée par le système d’exploitation. Elle n’est pas libérée, car le `CString` destructeur est appelé ; elle n’a pas encore été appelée. Elle est libérée simplement parce que l’application qui l’a allouée a quitté la scène. Désormais, si B `GetGlobalString(sz, sizeof(sz))` est appelé, il se peut que les données ne soient pas valides. Une autre application a peut-être utilisé cette mémoire pour un autre programme.

Il existe clairement un problème. MFC 3. x utilisait une technique appelée stockage local des threads (TLS). MFC 3. x allouerait un index TLS qui, sous Win32s, agit en réalité comme un index de stockage local de processus, même s’il n’est pas appelé, puis référencera toutes les données en fonction de cet index TLS. Cela est similaire à l’index TLS utilisé pour stocker des données locales de thread sur Win32 (voir ci-dessous pour plus d’informations sur ce sujet). Cela a entraîné l’utilisation par chaque DLL MFC d’au moins deux index TLS par processus. Quand vous comptez charger de nombreuses dll de contrôle OLE (ocx), vous exécutez rapidement des index TLS (il n’y a que 64 disponibles). En outre, les MFC devaient placer toutes ces données à un seul endroit, dans une structure unique. Il n’était pas très extensible et n’était pas idéal en ce qui concerne son utilisation des index TLS.

MFC 4. x y remédie avec un ensemble de modèles de classe que vous pouvez « encapsuler » autour des données qui doivent être traitées localement. Par exemple, le problème mentionné ci-dessus peut être résolu en écrivant :

```cpp
struct CMyGlobalData : public CNoTrackObject
{
    CString strGlobal;
};
CProcessLocal<CMyGlobalData> globalData;

__declspec(dllexport)
void SetGlobalString(LPCTSTR lpsz)
{
    globalData->strGlobal = lpsz;
}

__declspec(dllexport)
void GetGlobalString(LPCTSTR lpsz, size_t cb)
{
    StringCbCopy(lpsz, cb, globalData->strGlobal);
}
```

MFC implémente ce processus en deux étapes. Tout d’abord, il existe une couche au-dessus des API __\* TLS__ Win32 (**TlsAlloc**, **TlsSetValue**, **TlsGetValue**, etc.) qui utilisent uniquement deux index TLS par processus, quel que soit le nombre de dll dont vous disposez. Deuxièmement, le `CProcessLocal` modèle est fourni pour accéder à ces données. Elle remplace Operator-> qui permet la syntaxe intuitive que vous voyez ci-dessus. Tous les objets encapsulés par `CProcessLocal` doivent être dérivés de `CNoTrackObject` . `CNoTrackObject`fournit un allocateur de niveau inférieur (**LocalAlloc** / **LocalFree**) et un destructeur virtuel, de sorte que MFC peut supprimer automatiquement les objets locaux du processus lorsque le processus est terminé. Ces objets peuvent avoir un destructeur personnalisé si un nettoyage supplémentaire est nécessaire. L’exemple ci-dessus n’en requiert pas, car le compilateur génère un destructeur par défaut pour détruire l’objet incorporé `CString` .

Cette approche présente d’autres avantages intéressants. Non seulement tous les `CProcessLocal` objets sont détruits automatiquement, mais ils ne sont pas construits tant qu’ils ne sont pas nécessaires. `CProcessLocal::operator->` instancie l’objet associé la première fois qu’il est appelé, et pas plus tôt. Dans l’exemple ci-dessus, cela signifie que la `strGlobal` chaîne' 'ne sera pas construite avant la première fois `SetGlobalString` ou `GetGlobalString` est appelée. Dans certains cas, cela peut contribuer à réduire le temps de démarrage de la DLL.

## <a name="thread-local-data"></a>Données locales de thread

Comme pour traiter les données locales, les données locales de thread sont utilisées lorsque les données doivent être locales sur un thread donné. Autrement dit, vous avez besoin d’une instance distincte des données pour chaque thread qui accède à ces données. Ce nombre peut être utilisé à la place des mécanismes de synchronisation étendus. Si les données n’ont pas besoin d’être partagées par plusieurs threads, ces mécanismes peuvent être coûteux et inutiles. Supposons que nous disposions d’un `CString` objet (comme dans l’exemple ci-dessus). Nous pouvons le rendre thread local en l’encapsulant avec un `CThreadLocal` modèle :

```cpp
struct CMyThreadData : public CNoTrackObject
{
    CString strThread;
};
CThreadLocal<CMyThreadData> threadData;

void MakeRandomString()
{
    // a kind of card shuffle (not a great one)
    CString& str = threadData->strThread;
    str.Empty();
    while (str.GetLength() != 52)
    {
        unsigned int randomNumber;
        errno_t randErr;
        randErr = rand_s(&randomNumber);

        if (randErr == 0)
        {
            TCHAR ch = randomNumber % 52 + 1;
            if (str.Find(ch) <0)
            str += ch; // not found, add it
        }
    }
}
```

Si `MakeRandomString` a été appelé à partir de deux threads différents, chacun « aléatoire » la chaîne de différentes façons sans interférer avec l’autre. Cela est dû au fait qu’il existe réellement une `strThread` instance par thread au lieu d’une seule instance globale.

Notez comment une référence est utilisée pour capturer l' `CString` adresse une fois au lieu d’une fois par itération de boucle. Le code de boucle aurait pu être écrit avec `threadData->strThread` Everywhere « `str` », mais le code serait beaucoup plus lent en cours d’exécution. Il est préférable de mettre en cache une référence aux données lorsque de telles références se produisent dans des boucles.

Le `CThreadLocal` modèle de classe utilise les mêmes mécanismes que ceux utilisés par `CProcessLocal` et les mêmes techniques d’implémentation.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
