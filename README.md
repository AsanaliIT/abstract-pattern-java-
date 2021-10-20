public abstract class AbstractFood {

    public abstract String getItemName();
    public abstract boolean isDelivered();
    public abstract int getQuantity();
     
}

public class ItalianFood extends AbstractFood {

    String itemName;
    int quantity;
    boolean delivered;
     
    public String getItemName() {
    
        return itemName;
    }
    
 
    public void setItemName(String itemName) {
    
        this.itemName = itemName;
        
    }
 
    public int getQuantity() {
    
        return quantity;
        
    }
 
    public void setQuantity(int quantity) {
    
        this.quantity = quantity;
        
    }
 
    public boolean isDelivered() {
    
        return delivered;
    }
 
    public void setDelivered(boolean delivered) {
        this.delivered = delivered;
    }
 
}


public class MexicanFood extends AbstractFood {

    String itemName;
    int quantity;
    boolean delivered;
 
    public String getItemName() {
    
        return itemName;
    }
 
    public void setItemName(String itemName) {
    
        this.itemName = itemName;
    }
 
    public int getQuantity() {
    
        return quantity;
    }
 
    public void setQuantity(int quantity) {
    
        this.quantity = quantity;
    }
 
    public boolean isDelivered() {
    
        return delivered;
    }
 
    public void setDelivered(boolean delivered) {
    
        this.delivered = delivered;
    }
 
}




public abstract class AbstractFoodFactory {

    public abstract AbstractFoodFactory placeOrder(String itemName, int quantity) ;
}

public class ItalianFoodFactory extends AbstractFoodFactory {

   @Override
    public AbstractFood placeOrder(String itemName, int quantity) {
    
        return new ItalianFood(itemName,quantity);
    }
 }
 
 public class MexicanFoodFactory extends AbstractFoodFactory {
 
    @Override
    public AbstractFood placeOrder(String itemName, int quantity) {
    
        return new MexicanFood(itemName,quantity);
    }
}


public class ConsumerClass {

    public AbstractFood placeOrder(String itemName,int quantity,String itemType) {
    
        AbstractFoodFactory a = null;
        if(itemType.equals("italian")) {
        
            a = new ItalianFoodFactory();
        }else if(itemType.equals("mexican")) {
        
            a = new MexicanFoodFactory();
        }
        if(a!=null) {
        
            return a.placeOrder(itemName, quantity);
        }else {
        
            return null;
        }
    }
}
 
