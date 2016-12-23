```java
// Konkretes Subjekt
class PostServer extends Observable {
  private String message;

  public String getMessage() {
    return message;
  }

  public void changeMessage(String message) {
    this.message = message;
    setChanged();
    notifyObservers(message);
  }

  public static void main(String[] args) {
    // Konkretes Subjekt erstellen (Observable)
    PostServer server = new PostServer();

    // Konkrete Observer erstellen
    PostClient client1 = new PostClient();
    PostClient client2 = new PostClient();
    PostClient client3 = new PostClient();
    PostClient client4 = new PostClient();

    // Die Clients in die Observer-Liste packen
    server.addObserver(client1);
    server.addObserver(client2);
    server.addObserver(client1);
    server.addObserver(client1);

    // nun bekommen dies alle hinzugefügten Clients mit und
    // geben es schlussendlich in der Kommandozeile aus weil ihre
    // update Methode aufgerufen wird
    server.changeMessage("Hello Players!");
  }
}

// Konkreter Beobachter
class PostClient implements Observer {
  public void update(Observable o, Object arg) {
    System.out.println(arg);
  }
}
```
