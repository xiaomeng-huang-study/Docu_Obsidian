Der Waypoint Follower (auf Deutsch: Wegpunkte-Folger) ist ein ROS-Knoten (Node), der es ermöglicht, einen Roboter auf einem vordefinierten Pfad zu bewegen. Der Knoten abonniert (subscribed) auf einen ROS-Topic, auf dem eine Liste von Wegpunkten (Positionen im Raum) veröffentlicht wird, die der Roboter in einer bestimmten Reihenfolge abfahren soll.

Sobald der Knoten die Liste der Wegpunkte empfangen hat, beginnt er, den Roboter zu steuern, indem er kontinuierlich die aktuellen Roboterpositionen mit der Liste der Wegpunkte vergleicht und den Roboter entsprechend steuert, um ihn zum nächsten Wegpunkt zu führen. Dabei wird in der Regel ein Regelungsverfahren wie ein PID-Regler oder ein anderer Regler verwendet, um den Roboter auf Kurs zu halten.

Der Waypoint Follower ist ein grundlegender Bestandteil vieler Navigationssysteme, da er es ermöglicht, vordefinierte Pfade abzufahren, die z.B. von einem Benutzer oder einem anderen Knoten bereitgestellt werden können.