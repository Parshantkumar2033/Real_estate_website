# **Database Schema for Real Estate DBMS**

## 1. **Residential_Seller**
| Feature                  | Data Type        | Description              |
|--------------------------|------------------|--------------------------|
| **Property_ID**           | INT              | Primary Key              |
| Aadhaar_number            | VARCHAR(12)      |                          |
| name                      | VARCHAR(100)     |                          |
| type                      | VARCHAR(50)      |                          |
| space                     | INT              | Size of the property in sq. ft. |
| amount_non_furnished       | DECIMAL(10, 2)   |                          |
| amount_semi_furnished      | DECIMAL(10, 2)   |                          |
| amount_full_furnished      | DECIMAL(10, 2)   |                          |
| city                      | VARCHAR(100)     |                          |
| locality                  | VARCHAR(100)     |                          |
| status                    | VARCHAR(50)      |                          |

### Primary Key: 
- **Property_ID**
_________________________________________________________________________________________________

## 2. **Residential_Property_Details**
| Feature                  | Data Type        | Description              |
|--------------------------|------------------|--------------------------|
| **RS_Property_ID**        | INT              | Primary Key              |
| **RS_Aadhar_number**      | VARCHAR(12)      |                          |
| **RP_Property_ID**        | INT              | Foreign Key (Residential_Property.Property_ID) |
| **RP_Aadhar_number**      | VARCHAR(12)      | Foreign Key (Residential_Buyer.Aadhaar_number) |

### Primary Key: 
- **RS_Property_ID**, **RS_Aadhar_number**

### Foreign Key: 
- **RP_Property_ID** references Residential_Property(Property_ID)
- **RP_Aadhar_number** references Residential_Buyer(Aadhaar_number)

---

## 3. **Residential_Property**
| Feature                  | Data Type        | Description              |
|--------------------------|------------------|--------------------------|
| **Property_ID**           | INT              | Primary Key              |
| Aadhaar_number            | VARCHAR(12)      | Foreign Key (Residential_Seller.Aadhaar_number) |
| type                      | VARCHAR(50)      |                          |
| space                     | INT              |                          |
| amount                    | DECIMAL(10, 2)   |                          |
| city                      | VARCHAR(100)     |                          |
| locality                  | VARCHAR(100)     |                          |
| status                    | VARCHAR(50)      |                          |
| date                      | DATE             | Date of listing          |

### Primary Key: 
- **Property_ID**

### Foreign Key: 
- **Aadhaar_number** references Residential_Seller(Aadhaar_number)

---

## 4. **Residential_Buyer**
| Feature                  | Data Type        | Description              |
|--------------------------|------------------|--------------------------|
| **Buyer_ID**              | INT              | Primary Key              |
| Aadhaar_number            | VARCHAR(12)      |                          |
| name                      | VARCHAR(100)     |                          |
| requirement               | VARCHAR(255)     |                          |
| city                      | VARCHAR(100)     |                          |
| budget                    | DECIMAL(10, 2)   |                          |
| furnishing_status          | VARCHAR(50)      |                          |
| Buy_rent                  | VARCHAR(50)      | Purchase or rent         |

### Primary Key: 
- **Buyer_ID**

---

## 5. **Commercial_Seller**
| Feature                  | Data Type        | Description              |
|--------------------------|------------------|--------------------------|
| **Property_ID**           | INT              | Primary Key              |
| Aadhaar_number            | VARCHAR(12)      |                          |
| name                      | VARCHAR(100)     |                          |
| type                      | VARCHAR(50)      |                          |
| area                      | INT              | Size of the property in sq. ft. |
| amount                    | DECIMAL(10, 2)   |                          |
| amount_restaurant         | DECIMAL(10, 2)   |                          |
| amount_multiplex          | DECIMAL(10, 2)   |                          |
| amount_food_court         | DECIMAL(10, 2)   |                          |
| city                      | VARCHAR(100)     |                          |
| locality                  | VARCHAR(100)     |                          |
| status                    | VARCHAR(50)      |                          |

### Primary Key: 
- **Property_ID**

---

## 6. **Commercial_Property_Details**
| Feature                  | Data Type        | Description              |
|--------------------------|------------------|--------------------------|
| **CS_Property_ID**        | INT              | Primary Key              |
| **CS_Aadhar_number**      | VARCHAR(12)      |                          |
| **CP_Property_ID**        | INT              | Foreign Key (Commercial_Property.Property_ID) |
| **CP_Aadhar_number**      | VARCHAR(12)      | Foreign Key (Commercial_Buyer.Aadhaar_number) |

### Primary Key: 
- **CS_Property_ID**, **CS_Aadhar_number**

### Foreign Key: 
- **CP_Property_ID** references Commercial_Property(Property_ID)
- **CP_Aadhar_number** references Commercial_Buyer(Aadhaar_number)

---

## 7. **Commercial_Property**
| Feature                  | Data Type        | Description              |
|--------------------------|------------------|--------------------------|
| **Property_ID**           | INT              | Primary Key              |
| Aadhaar_number            | VARCHAR(12)      | Foreign Key (Commercial_Seller.Aadhaar_number) |
| type                      | VARCHAR(50)      |                          |
| area                      | INT              |                          |
| amount                    | DECIMAL(10, 2)   |                          |
| city                      | VARCHAR(100)     |                          |
| locality                  | VARCHAR(100)     |                          |
| status                    | VARCHAR(50)      |                          |
| date                      | DATE             | Date of listing          |

### Primary Key: 
- **Property_ID**

### Foreign Key: 
- **Aadhaar_number** references Commercial_Seller(Aadhaar_number)

---

## 8. **Commercial_Buyer**
| Feature                  | Data Type        | Description              |
|--------------------------|------------------|--------------------------|
| **Buyer_ID**              | INT              | Primary Key              |
| Aadhaar_number            | VARCHAR(12)      |                          |
| name                      | VARCHAR(100)     |                          |
| requirement               | VARCHAR(255)     |                          |
| city                      | VARCHAR(100)     |                          |
| budget                    | DECIMAL(10, 2)   |                          |
| investment                | DECIMAL(10, 2)   | Investment amount        |
| area                      | INT              | Area requirement         |
| Buy_lease                 | VARCHAR(50)      | Purchase or lease        |

### Primary Key: 
- **Buyer_ID**

---

## 9. **Agent**
| Feature                  | Data Type        | Description              |
|--------------------------|------------------|--------------------------|
| **Agent_ID**              | INT              | Primary Key              |
| Aadhaar_number            | VARCHAR(12)      |                          |
| name                      | VARCHAR(100)     |                          |
| no_of_property            | INT              | Number of properties handled |
| average_amount            | DECIMAL(10, 2)   | Average amount handled   |

### Primary Key: 
- **Agent_ID**

---

## 10. **Transaction_records**
| Feature                  | Data Type        | Description              |
|--------------------------|------------------|--------------------------|
| **property_id**           | INT              | Primary Key              |
| **agent_id**              | INT              | Primary Key              |
| **buyer_id**              | INT              | Primary Key              |
| date                      | DATE             | Transaction date         |
| amount                    | DECIMAL(10, 2)   | Transaction amount       |
| type                      | VARCHAR(50)      | Sale or rent             |

### Primary Key: 
- **property_id**, **agent_id**, **buyer_id**

### Foreign Key: 
- **agent_id** references Agent(Agent_ID)
- **buyer_id** references Residential_Buyer(Buyer_ID) or Commercial_Buyer(Buyer_ID)
