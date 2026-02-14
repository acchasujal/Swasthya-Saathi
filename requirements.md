# Requirements Document: Swaasthya Sathi

## Feature Name
Swaasthya Sathi - India-First Health Intelligence Platform

## Introduction

Swaasthya Sathi is an "India-First" health intelligence platform that serves as a "Personalized AI Nutritionist & Safety Guardian" designed for the Indian population. Unlike generic calorie counters or label scanners, it uses Generative AI through Amazon Bedrock to map food and cosmetic ingredients to a user's Bio-Individual Health Profile (e.g., Diabetes, Hypertension, Skin Sensitivity), providing personalized safety verdicts in vernacular Indian languages.

The platform addresses the critical gap between generic health advice and personalized health intelligence, recognizing that a "Healthy High-Protein Bar" may be dangerous for a kidney patient while being beneficial for a gym enthusiast.

## The Burning Problem

**Health-Washing Crisis**: Many Indian products claim to be "Healthy" or "Natural" but hide sugars (e.g., Maltodextrin) and endocrine disruptors (e.g., Parabens) under complex chemical names, exploiting consumer trust.

**Lifestyle Disease Epidemic**: India is the "Diabetes Capital" with over 77 million diabetics, yet consumers cannot easily identify ingredients that spike insulin, blood pressure, or trigger other health complications.

**Language & Literacy Barrier**: Fine print on labels is inaccessible to 90% of Indians who cannot read complex English ingredient lists, particularly affecting the elderly and semi-literate populations in Bharat.

**Generic vs. Bio-Individual Context**: Existing health apps provide one-size-fits-all advice, missing the critical context that the same ingredient can be safe for one person but dangerous for another based on their unique health profile.

## User Personas

### Primary Personas

**1. Priya Sharma - The Health-Conscious Mother (Age: 35)**
- Location: Tier-2 city (Indore)
- Profile: Working mother with two children, one with lactose intolerance
- Pain Points: Struggles to identify hidden dairy ingredients, limited time for detailed label reading
- Goals: Ensure family's food safety, teach children healthy eating habits
- Technology Comfort: Moderate smartphone user, prefers Hindi interface

**2. Rajesh Kumar - The Diabetic Senior (Age: 62)**
- Location: Tier-3 city (Kanpur)
- Profile: Retired government employee, Type 2 diabetes for 8 years
- Pain Points: Cannot read small English text, confused by sugar alternatives
- Goals: Manage blood sugar levels, avoid complications
- Technology Comfort: Basic smartphone user, needs audio assistance

**3. Ananya Patel - The Fitness Enthusiast (Age: 28)**
- Location: Metro city (Mumbai)
- Profile: Software engineer, gym regular, PCOD management
- Pain Points: Wants high-protein foods but needs to avoid certain additives
- Goals: Optimize nutrition for fitness goals while managing hormonal health
- Technology Comfort: Tech-savvy, expects quick and accurate results

**4. Dr. Meera Reddy - The Hypertensive Professional (Age: 45)**
- Location: Metro city (Bangalore)
- Profile: Cardiologist with hypertension, ironic but common
- Pain Points: Needs to monitor sodium intake strictly, limited time for shopping
- Goals: Maintain professional credibility while managing personal health
- Technology Comfort: High, values scientific accuracy

### Secondary Personas

**5. Ramesh Gupta - The Rural Shopkeeper (Age: 50)**
- Location: Rural area (Haryana)
- Profile: Runs local grocery store, wants to help customers make informed choices
- Pain Points: Limited health knowledge, customers ask for advice
- Goals: Build customer trust, increase sales of healthier products
- Technology Comfort: Basic, needs simple interface

## Glossary

**System**: The Swaasthya Sathi application

**Health_Passport**: User's comprehensive bio-individual health profile including conditions, allergies, and dietary restrictions

**Bio_Individual_Score**: Dynamic safety score (0-100) calculated based on user's unique health profile

**Hidden_Enemy**: Ingredients with complex chemical names that mask common harmful substances

**E_Code**: European food additive numbering system (e.g., E621 for MSG)

**Agentic_Multimodal_Scanning**: AI-powered combination of computer vision and reasoning for comprehensive product analysis

**Audio_Advisory**: Text-to-speech component for vernacular language warnings ("Suniye" feature)

**PWA**: Progressive Web Application for offline-first mobile experience

**Health_Washing**: Marketing practice of making products appear healthier than they actually are

**Vernacular_Accessibility**: Multi-language support for regional Indian languages

**Tier_3_Connectivity**: Network conditions typical in smaller Indian cities with intermittent internet

## Success Metrics

**User Adoption Metrics**:
- Target 100,000 active users within first 6 months of launch
- 70% user retention rate after first month
- Average 5+ product scans per user per week

**Accuracy Metrics**:
- 95%+ OCR accuracy for ingredient text extraction
- 90%+ user satisfaction with bio-individual scoring relevance
- 85%+ accuracy in hidden ingredient detection

**Performance Metrics**:
- Sub-10 second analysis time for 95% of scans
- 99.5% uptime during peak usage hours
- Offline functionality for 100% of previously scanned products

**Health Impact Metrics**:
- 60%+ users report making healthier purchasing decisions
- 40%+ users with chronic conditions report better health management
- Measurable reduction in consumption of harmful ingredients among active users

## Out of Scope

The following items are explicitly out of scope for the initial release:

- Medical diagnosis or treatment recommendations
- Prescription medication analysis or drug interactions
- Restaurant menu analysis or dining recommendations
- Nutritional meal planning or calorie tracking features
- Social features like product reviews or community forums
- E-commerce integration or product purchasing capabilities
- Wearable device integration or health metric tracking
- Recipe suggestions or cooking instructions
- Barcode-based product lookup (focus is on ingredient analysis)
- International product databases (India-focused initially)

## Requirements

### Requirement 1: Bio-Individual Health Passport Creation

**User Story:** As a user, I want to create and manage my personalized "Health Passport" with my chronic conditions and allergies, so that I can receive tailored safety assessments that understand my unique health context.

#### Acceptance Criteria

1. WHEN a new user opens the app, THE System SHALL display a localized health passport onboarding flow in the user's preferred language
2. WHEN creating a health passport, THE System SHALL allow selection of multiple chronic conditions from a predefined list including Diabetes, Hypertension, PCOD, Heart Health, Kidney Disease, and Thyroid Disorders
3. WHEN creating a health passport, THE System SHALL allow selection of allergies from a comprehensive list including Gluten, Lactose, Nuts, Shellfish, Soy, and custom allergen input
4. WHEN a user updates their health passport, THE System SHALL recalculate all previously analyzed product scores and notify the user of changes
5. THE System SHALL encrypt and securely store all health passport data in compliance with Indian privacy guidelines and Responsible AI principles
6. WHEN onboarding, THE System SHALL explain that it provides health intelligence, not medical diagnosis, and recommend consulting healthcare professionals

### Requirement 2: Agentic Multimodal Product Scanning

**User Story:** As a user, I want to scan product packaging using advanced AI-powered vision and reasoning, so that I can analyze ingredients from curved, shiny, or crinkled packaging without manual typing.

#### Acceptance Criteria

1. WHEN a user captures an image of product packaging, THE System SHALL use Amazon Textract for robust OCR to extract text from curved, shiny, or crinkled surfaces
2. WHEN text extraction is complete, THE System SHALL use Amazon Bedrock (Claude 3.5 Sonnet) to intelligently identify and parse ingredient lists within the extracted text
3. WHEN ingredient lists are identified, THE System SHALL use AI reasoning to parse individual ingredients, their quantities, and understand context-dependent ingredient relationships
4. IF text extraction fails or is incomplete, THEN THE System SHALL provide intelligent guidance for optimal image capture and offer manual input as fallback
5. THE System SHALL support analysis of both food and cosmetic product packaging with category-specific ingredient understanding
6. WHEN processing images, THE System SHALL work offline-first by caching analysis capabilities for previously scanned products

### Requirement 3: Dynamic Bio-Individual Scoring Engine

**User Story:** As a user with specific health conditions, I want to receive personalized "Red/Green Shield" safety scores that change based on MY unique health profile, so that I understand why a product is safe or unsafe specifically for me.

#### Acceptance Criteria

1. WHEN ingredients are analyzed, THE System SHALL calculate a Bio_Individual_Score between 0 and 100 using Amazon Bedrock's reasoning capabilities combined with the user's Health_Passport
2. WHEN a user has diabetes, THE System SHALL penalize ingredients with high glycemic index values and hidden sugars, providing specific explanations like "Unsafe for YOU because of High Sugar Content"
3. WHEN a user has hypertension, THE System SHALL penalize high sodium content and specific additives, with explanations like "High Risk due to Sodium Levels exceeding your daily limit"
4. WHEN a user has allergies, THE System SHALL assign zero score to products containing those allergens with urgent warnings
5. THE System SHALL demonstrate that the same product receives different scores when analyzed by users with different health profiles, showing the bio-individual nature
6. WHEN displaying scores, THE System SHALL use clear visual indicators: Green Shield (Safe), Yellow Shield (Moderate Risk), Red Shield (High Risk)
7. THE System SHALL provide contextual explanations for each score, helping users understand the "why" behind the recommendation

### Requirement 4: Hidden Enemy Detection

**User Story:** As a consumer, I want to identify harmful ingredients hidden behind complex chemical names, so that I can avoid products that may negatively impact my health.

#### Acceptance Criteria

1. WHEN analyzing ingredients, THE System SHALL decode E_Codes to their common names and health implications
2. WHEN detecting hidden sugars, THE System SHALL identify and flag ingredients like Maltodextrin, High Fructose Corn Syrup, and Dextrose
3. WHEN detecting endocrine disruptors, THE System SHALL identify and flag ingredients like Parabens, Phthalates, and BPA
4. WHEN harmful ingredients are detected, THE System SHALL provide clear explanations of their health risks
5. THE System SHALL maintain an updated database of ingredient mappings and health implications
6. THE System SHALL provide clear explanations of health risks for each detected harmful ingredient

### Requirement 5: Vernacular "Suniye" Audio Advisory

**User Story:** As a user who prefers regional languages or has difficulty reading, I want to receive spoken warnings and advice through the "Suniye" feature in my preferred Indian language, so that I can understand product safety information regardless of my literacy level.

#### Acceptance Criteria

1. WHEN a product analysis is complete, THE System SHALL use Amazon Polly to provide spoken summaries in the user's selected regional language through the "Suniye" feature
2. THE System SHALL support Hindi, Marathi, and English (Indian accent) with neural-quality voices, with extensibility for other major Indian regional languages
3. WHEN high-risk ingredients are detected, THE Audio_Advisory SHALL provide urgent warnings in simple, clear language appropriate for elderly users and varying literacy levels
4. WHEN providing audio feedback, THE System SHALL use culturally appropriate language and references familiar to Indian users
5. THE System SHALL allow users to replay audio advisories, adjust speech speed, and pause/resume playback
6. THE Audio_Advisory SHALL work offline for previously analyzed products to support Tier-3 city connectivity constraints

### Requirement 6: Product Safety Scoring and Recommendations

**User Story:** As a health-conscious consumer, I want clear safety recommendations and alternative suggestions, so that I can make better product choices.

#### Acceptance Criteria

1. WHEN displaying product analysis results, THE System SHALL show the Bio_Individual_Score prominently with color-coded safety levels
2. WHEN a product receives a low safety score, THE System SHALL explain the specific reasons for the low rating
3. WHEN harmful ingredients are detected, THE System SHALL suggest healthier alternative products when available
4. THE System SHALL categorize safety levels as Safe (80-100), Moderate Risk (50-79), and High Risk (0-49)
5. THE System SHALL provide actionable recommendations for each safety category

### Requirement 7: Data Privacy and Security

**User Story:** As a user sharing sensitive health information, I want my data to be protected and handled responsibly, so that my privacy is maintained.

#### Acceptance Criteria

1. THE System SHALL encrypt all Health_Profile data both in transit and at rest
2. WHEN storing user data, THE System SHALL comply with applicable privacy regulations and Responsible AI guidelines
3. THE System SHALL not share user health information with third parties without explicit consent
4. WHEN processing images, THE System SHALL not store captured product images permanently
5. THE System SHALL provide users with options to delete their health profiles and associated data

### Requirement 8: Performance and Reliability

**User Story:** As a user in various network conditions across India, I want the app to work reliably and quickly, so that I can make timely purchasing decisions.

#### Acceptance Criteria

1. WHEN analyzing a product image, THE System SHALL provide results within 10 seconds under normal network conditions
2. WHEN network connectivity is poor, THE System SHALL provide offline capabilities for previously analyzed products
3. THE System SHALL handle concurrent user requests without performance degradation
4. WHEN system errors occur, THE System SHALL provide clear error messages and recovery options
5. THE System SHALL maintain 99.5% uptime during peak usage hours

### Requirement 9: Ingredient Database Management

**User Story:** As a system administrator, I want to maintain an accurate and up-to-date ingredient database, so that users receive current and reliable health information.

#### Acceptance Criteria

1. THE System SHALL maintain a comprehensive database of food and cosmetic ingredients with health impact data
2. WHEN new ingredients are discovered, THE System SHALL allow database updates without requiring app updates
3. THE System SHALL validate ingredient data against authoritative health and nutrition sources
4. WHEN ingredient health impacts change based on new research, THE System SHALL update recommendations accordingly
5. THE System SHALL track ingredient database version and update history for audit purposes

### Requirement 10: User Interface and Experience

**User Story:** As a user, I want an intuitive and accessible interface that works seamlessly across devices, so that I can easily analyze products regardless of my technical expertise.

#### Acceptance Criteria

1. THE System SHALL provide a mobile-first responsive design optimized for Indian smartphone market
2. THE System SHALL support both portrait and landscape orientations for camera scanning
3. WHEN displaying analysis results, THE System SHALL use clear visual hierarchy with color-coded safety indicators
4. THE System SHALL provide contextual help and tooltips for first-time users
5. THE System SHALL support accessibility features including screen reader compatibility and high contrast mode
6. WHEN users interact with the app, THE System SHALL provide immediate visual feedback for all actions
7. THE System SHALL minimize the number of steps required to complete a product scan (target: 2 taps from home to results)

### Requirement 11: Offline-First PWA Architecture

**User Story:** As a user in Tier-3 cities with intermittent connectivity, I want the app to work offline and sync when online, so that I can make purchasing decisions even with poor network conditions.

#### Acceptance Criteria

1. THE System SHALL be implemented as a Progressive Web App (PWA) that works offline-first
2. WHEN offline, THE System SHALL provide access to previously analyzed products and user health passport data
3. WHEN connectivity is restored, THE System SHALL automatically sync new analyses and profile updates
4. THE System SHALL store user profiles locally with encryption and sync securely when online
5. WHEN network is unavailable, THE System SHALL clearly indicate offline mode and available functionality
6. THE System SHALL prioritize essential safety information for offline access, ensuring critical health warnings are always available

### Requirement 12: Responsible AI and Medical Disclaimer

**User Story:** As a health-conscious user, I want clear understanding that the app provides health intelligence and not medical diagnosis, so that I can use it appropriately as a decision-support tool.

#### Acceptance Criteria

1. THE System SHALL prominently display disclaimers that it provides health intelligence, not medical diagnosis
2. WHEN providing health-related recommendations, THE System SHALL encourage users to consult healthcare professionals for medical decisions
3. THE System SHALL avoid making definitive medical claims and use language like "may be suitable" or "consider avoiding"
4. WHEN detecting severe allergens or high-risk ingredients, THE System SHALL recommend immediate medical consultation if needed
5. THE System SHALL maintain transparency about AI decision-making and provide sources for health claims when possible
6. THE System SHALL comply with Indian healthcare regulations and responsible AI guidelines for health applications


## Assumptions and Dependencies

**Assumptions**:
- Users have access to smartphones with camera capabilities (Android 8.0+ or iOS 12+)
- Users have intermittent or consistent internet connectivity for initial setup and periodic syncing
- Users can provide basic health information accurately during onboarding
- Product packaging in India contains readable ingredient lists as per FSSAI regulations
- Users understand that the app provides health intelligence, not medical diagnosis

**Dependencies**:
- AWS Services: Amazon Bedrock (Claude 3.5 Sonnet), Amazon Textract, Amazon Polly, AWS Lambda, DynamoDB, Cognito
- FSSAI ingredient database and regulatory guidelines for Indian food products
- Reliable ingredient health impact research and scientific literature
- Third-party libraries for PWA functionality and offline storage
- Indian language neural voice models availability in Amazon Polly
- Stable AWS service availability in Indian regions

**Risks and Mitigations**:
- Risk: AI hallucination in ingredient analysis → Mitigation: Cross-validation with ingredient database and confidence scoring
- Risk: OCR failure on poor quality images → Mitigation: Image quality guidance and manual input fallback
- Risk: User misinterpretation of health advice → Mitigation: Clear disclaimers and medical consultation recommendations
- Risk: Privacy concerns with health data → Mitigation: Strong encryption, transparent privacy policy, user data control
- Risk: Network connectivity issues in Tier-3 cities → Mitigation: Offline-first architecture with intelligent caching
- Risk: Cultural insensitivity in audio advisories → Mitigation: Native speaker validation and cultural context testing

## Acceptance Criteria Summary

This requirements document defines 12 major functional areas with 73 specific acceptance criteria that must be validated during testing. Each requirement includes clear user stories and measurable acceptance criteria to ensure the system meets user needs while maintaining safety, privacy, and cultural appropriateness for the Indian market.
