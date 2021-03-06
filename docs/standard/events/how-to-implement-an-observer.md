---
title: 'Gewusst wie: Implementieren eines Observers'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- observers [.NET Framework], observer design pattern
- observer design pattern [.NET Framework], implementing observers
ms.assetid: 8ecfa9f5-b500-473d-bcf0-5652ffb1e53d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6426e8bd138d06d3655562de6384e46a12c09279
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2018
ms.locfileid: "48583986"
---
# <a name="how-to-implement-an-observer"></a>Gewusst wie: Implementieren eines Observers
Das Entwurfsmuster „Observer“ erfordert eine Trennung zwischen einem Observer, der für den Empfang von Benachrichtigungen registriert wird, und einem Anbieter, der Daten überwacht und Benachrichtigungen an mindestens einen Observer sendet. In diesem Thema wird das Erstellen eines Observers behandelt. In dem verwandten Thema [Gewusst wie: Implementieren eines Anbieters](../../../docs/standard/events/how-to-implement-a-provider.md) wird erläutert, wie ein Anbieter erstellt wird.  
  
### <a name="to-create-an-observer"></a>So erstellen Sie einen Observer  
  
1.  Definieren Sie den Observer, der einen Typ zur Implementierung der <xref:System.IObserver%601?displayProperty=nameWithType>-Schnittstelle aufweist. Der folgende Code definiert z.B. einen Typ namens `TemperatureReporter`, der eine erstellte <xref:System.IObserver%601?displayProperty=nameWithType>-Implementierung mit einem generischen Typargument von `Temperature` darstellt.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2.  Wenn der Observer den Empfang von Benachrichtigungen beenden kann, bevor der Anbieter seine <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>-Implementierung aufruft, definieren Sie eine private Variable, die die von der <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType>-Methode des Anbieters zurückgegebene <xref:System.IDisposable>-Implementierung enthalten soll. Sie sollten auch eine Abonnementmethode definieren, die die <xref:System.IObservable%601.Subscribe%2A>-Methode des Anbieters aufruft und das zurückgegebene <xref:System.IDisposable>-Objekt speichert. Der folgende Code definiert z.B. eine private Variable mit dem Namen `unsubscriber` und definiert eine `Subscribe`-Methode, die die <xref:System.IObservable%601.Subscribe%2A>-Methode des Anbieters aufruft und das zurückgegebene Objekt der `unsubscriber`-Variable zuweist.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3.  Wenn dieses Feature erforderlich sein sollte, definieren Sie eine Methode, die dem Observer das Beenden des Benachrichtigungsempfangs ermöglicht, bevor der Anbieter die jeweilige <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>-Implementierung aufruft. Im folgenden Beispiel wird eine `Unsubscribe`-Methode definiert.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4.  Stellen Sie Implementierungen der drei durch die <xref:System.IObserver%601>-Schnittstelle definierten Methoden bereit: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, und <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>. Je nach Anbieter und den Anforderungen der Anwendung, kann es sich bei der <xref:System.IObserver%601.OnError%2A>- und <xref:System.IObserver%601.OnCompleted%2A>-Methode um Stubimplementierungen handeln. Hinweis: Die <xref:System.IObserver%601.OnError%2A>-Methode sollte das übergebene <xref:System.Exception>-Objekt nicht als Ausnahme behandeln, und die <xref:System.IObserver%601.OnCompleted%2A>-Methode kann nach Bedarf die <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>-Implementierung des Anbieters aufrufen. Im folgenden Beispiel wird die `TemperatureReporter`-Implementierung der <xref:System.IObserver%601>-Klasse veranschaulicht.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel enthält den vollständigen Quellcode für die `TemperatureReporter`-Klasse, um die <xref:System.IObserver%601>-Implementierung für eine Anwendung zur Temperaturüberwachung zu definieren.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a>Siehe auch

- <xref:System.IObserver%601>  
- [Beobachterentwurfsmuster](../../../docs/standard/events/observer-design-pattern.md)  
- [Gewusst wie: Implementieren eines Anbieters](../../../docs/standard/events/how-to-implement-a-provider.md)  
- [Empfohlene Vorgehensweisen für Beobachterentwurfsmuster](../../../docs/standard/events/observer-design-pattern-best-practices.md)
